---
title: "is possible to start a application with default arguments?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by Vichfret on 2010-06-17
I want to start gnome-mplayer always with some default arguments 

```

vicfred@Elain ~ % gnome-mplayer --help                                                                           <0:44>
Usage:
  gnome-mplayer [OPTION...] [FILES...] - GNOME Media player based on MPlayer

Help Options:
  -?, --help                        Show help options
  --help-all                        Show all help options
  --help-gtk                        Show GTK+ Options

Application Options:
  --window=WID                      Window to embed in
  -w, --width=X                     Width of window to embed in
  -h, --height=Y                    Height of window to embed in
  --controlid=CID                   Unique DBUS controller id
  --playlist                        File Argument is a playlist
  -v, --verbose                     Show more output on the console
  --reallyverbose                   Show even more output on the console
  --fullscreen                      Start in fullscreen mode
  --softvol                         Use mplayer software volume control
  --remember_softvol                When set to TRUE the last volume level is set as the default
  --volume_softvol                  Last software volume percentage- only applied when remember_softvol is set to TRUE
  --mixer                           Mixer to use
  --volume                          Set initial volume percentage
  --showcontrols=[0|1]              Show the controls in window
  --showsubtitles=[0|1]             Show the subtitles if available
  --autostart=[0|1]                 Autostart the media default to 1, set to 0 to load but don't play
  --disablecontextmenu              Disable popup menu on right click
  --disablefullscreen               Disable fullscreen options in browser mode
  --loop                            Play all files on the playlist forever
  -q, --quit_on_complete            Quit application when last file on playlist is played
  --random                          Play items on playlist in random order
  --cache                           Set cache size
  --ss                              Start Second (default to 0)
  --endpos                          Length of media to play from start second
  --forcecache                      Force cache usage on streaming sites
  --disabledeinterlace              Disable the deinterlace filter
  --disableframedrop                Don't skip drawing frames to better keep sync
  --disableass                      Use the old subtitle rendering system
  --disableembeddedfonts            Don't use fonts embedded on matroska files
  --vertical                        Use Vertical Layout
  --showplaylist                    Start with playlist open
  --showdetails                     Start with details visible
  --rpname=NAME                     Real Player Name
  --rpconsole=CONSOLE               Real Player Console ID
  --rpcontrols=Control Name,...     Real Player Console Controls
  --subtitle=FILENAME               Subtitle file for first media file
  --tvdevice=DEVICE                 TV device name
  --tvdriver=DRIVER                 TV driver name (v4l|v4l2)
  --tvinput=INPUT                   TV input name
  --tvwidth=WIDTH                   Width of TV input
  --tvheight=HEIGHT                 Height of TV input
  --tvfps=FPS                       Frames per second from TV input
  --single_instance                 Only allow one instance
  --replace_and_play                Put single instance mode into replace and play mode
  --large_buttons                   Use large control buttons
  --always_hide_after_timeout       Hide control panel when mouse is not moving
  --new_instance                    Ignore single instance preference for this instance
  --keep_on_top                     Keep window on top
  --disable_cover_art_fetch         Don't fetch new cover art images
  --display=DISPLAY                 X display to use


```

In this case --loop and --showcontrols=0 but I do not want to launch gnome-mplayer always using a launcher but to set the defaults arguments when I launch a video, is there a way to do this?

---

### Post by bruno9779 on 2010-06-17
You can create an alias.

Smplayer also has a gui where the default arguments can be defined. I am not too sure about Mplayer gui, but since Smplayer is just a frontend, maybe that would work best for you

---

