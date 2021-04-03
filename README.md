# Google Calendar

Google Calendar desktop client for linux.

# Installation

You need to have the latest version of [docker](https://docs.docker.com/get-docker/) installed.

You will have to clone the repository.

```bash
git clone git@github.com:tjventurini/google-calendar.git
```

Next you will have pull the [nativefier](https://github.com/nativefier/nativefier) container in order to build the application.

```bash
docker pull nativefier/nativefier
```

Now you can build the electron application using the following command.

```bash
docker run --rm -v /path/to/google-calendar-repo:/src -v /tmp:/target nativefier/nativefier --icon /src/icon.png --name google-calendar -p linux -a x64 --single-instance --user-agent "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:87.0) Gecko/20100101 Firefox/87.0" --internal-urls ".*?\.google\.*?" https://google-calendar.com/ /target/
```

Now you can copy the build wherever you want.

```bash
mv /tmp/google-calendar-linux-x64 ~/apps/google-calendar
```

Now you can add an app launcher as shown below and store it under `~/.local/share/applications/google-calendar.desktop`.

```
[Desktop Entry]
Type=Application
Version=1.0
Exec=/home/username/apps/google-calendar/google-calendar
Name=Google Calendar
Comment=Custom google-calendar client for linux.
Icon=/home/username/apps/google-calendar/icon.png
Terminal=false
Categories=Media
```

Don't forget to refresh the database of application entries afterwards 😉

```bash
update-desktop-database ~/.local/share/applications
```