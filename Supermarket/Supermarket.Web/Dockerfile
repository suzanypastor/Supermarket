#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

#FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
#WORKDIR /app
#EXPOSE 80
#EXPOSE 443

#FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
#WORKDIR /src
#COPY ["Supermarket.Web/Supermarket.Web.csproj", "Supermarket.Web/"]
#RUN dotnet restore "Supermarket.Web/Supermarket.Web.csproj"
#COPY . .
#WORKDIR "/src/Supermarket.Web"
#RUN dotnet build "Supermarket.Web.csproj" -c Release -o /app/build

#FROM build AS publish
#RUN dotnet publish "Supermarket.Web.csproj" -c Release -o /app/publish

#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "Supermarket.Web.dll"]

FROM microsoft/mssql-server-linux:latest
# Create work directory
RUN mkdir -p /usr/work
WORKDIR /usr/work
# Copy all scripts into working directory
COPY . /usr/work/
# Grant permissions for the import-data script to be executable
RUN chmod +x /usr/work/import-data.sh
EXPOSE 1433
CMD /bin/bash ./entrypoint.sh