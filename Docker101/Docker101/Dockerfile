FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as build

ARG BUILDCONFIG=RELEASE
ARG VERSION=1.0.0

COPY Docker101.csproj /build/

RUN dotnet restore ./build/Docker101.csproj

COPY . ./build/
WORKDIR /build/
RUN dotnet publish ./Docker101.csproj -c RELEASE -o out /p:Version=1.0.0

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app

COPY --from=build /build/out .

ENTRYPOINT ["dotnet", "Docker101.dll"] 