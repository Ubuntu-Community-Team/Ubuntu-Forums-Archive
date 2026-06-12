---
title: "gnome connections to running vnc server shows blank screen"
date: 2022-11-03
forum: Networking &amp; Wireless
---

### Post by hansgoldenrod on 2022-11-03
[COLOR=#222222][FONT=Verdana]I've  got Ubuntu 20.04.5 LTS, Gnome 3.36.8 running on an HP ProBook 4730s.  I'm trying to remotely access it via my home network from a System76  machine running Pop!_OS 22.04 LTS.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]On the HP machine:[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]1.  Settings -> Sharing -> Screen Sharing, it is enabled and the  check box for "Allow connections to control the screen" is checked. The  same window says I should be able to connect to vnc://erik-HP-ProBook-4730s.local .[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]2. In terminal, I execute ```
sudo x11vnc -localhost -once -nopw -auth guess -find
``` and the output is 
```
erik@erik-HP-ProBook-4730s:~$ sudo x11vnc -localhost -once -nopw -auth guess -find
[sudo] password for erik: 
03/11/2022 08:03:10 x11vnc version: 0.9.16 lastmod: 2019-01-05  pid: 32415
03/11/2022 08:03:10 
03/11/2022 08:03:10 wait_for_client: WAIT:cmd=FINDDISPLAY
03/11/2022 08:03:10 
03/11/2022 08:03:10 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
03/11/2022 08:03:10 
03/11/2022 08:03:10 Autoprobing TCP port 
03/11/2022 08:03:10 Autoprobing selected TCP port 5900
03/11/2022 08:03:10 Autoprobing TCP6 port 
03/11/2022 08:03:10 Autoprobing selected TCP6 port 5900
03/11/2022 08:03:10 listen6: bind: Address already in use
03/11/2022 08:03:10 Not listening on IPv6 interface.
03/11/2022 08:03:10 

The VNC desktop is:      erik-HP-ProBook-4730s:0
PORT=5900

```
[/FONT][/COLOR]The output of ```
xauth list 
```is 
```
erik@erik-HP-ProBook-4730s:~$ xauth list 
erik-HP-ProBook-4730s/unix:  MIT-MAGIC-COOKIE-1  6e9ed65843d0b5dda423d9be20e22b61
#ffff#6572696b2d48502d50726f426f6f6b2d3437333073#:  MIT-MAGIC-COOKIE-1  6e9ed65843d0b5dda423d9be20e22b61

```




[COLOR=#222222][FONT=Verdana]On  the System76 machine, I am using gnome connections. Sometimes it says  "Unable to connect to HP-ProBook-4730s.local:5900: Error resolving  "erik-HP-ProBook-4730s.local": Temporary failure in name resolution.  Other times, it seems to connect, but the window is completely black. I am able to ping the ip address of the HP machine and it responds. I've also tried to connect to vnc://192.168.0.131:5900 and it says connection refused. I tried Remmina and it won't even connect. [/FONT][/COLOR]

Is there anything I am doing wrong? Why isn't this working? 

[COLOR=#222222][FONT=Verdana]I also looked through [/FONT][/COLOR][https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)[COLOR=#222222][FONT=Verdana] and tried the [/FONT][/COLOR][URL="https://ubuntu.com/tutorials/access-remote-desktop#1-overview"]Remmina tutorial.


[/URL]

---

### Post by hansgoldenrod on 2022-11-05
Removing the `-localhost` enabled me to see the port open up, using `nmap`. But x11vnc could not find the `display` no matter what I tried. Finally I gave up with x11vnc because it seems it is no longer supported and the Karl Runge website is offline. I switched to tigervnc and got it to work using `tigervnc-scraping-server` and `x0vncserver`.

---

### Post by &amp;KyT$0P# on 2022-11-06
It's insecure to directly connect VNC.  TigerVNC's scraping server has an option to listen on a Unix socket, which you can tunnel through SSH for a secure remote connection (I do this myself).

Here's the command I use to start TigerVNC scraping server -
```
X0tigervnc -display [COLOR="#FF0000"]<display>[/COLOR] -localhost -rfbport -1 -rfbunixpath [COLOR="#FF0000"]</path/to/unix/socket/file>[/COLOR] -SecurityTypes None -RawKeyboard
```
Replace the red parts with relevant values for your system.  Refer to [FONT=Courier New]man X0tigervnc[/FONT] for more info on the above command and options.

Refer to [FONT=Courier New]man ssh[/FONT] for how to use [FONT=Courier New]-L[/FONT] option of [FONT=Courier New]ssh[/FONT] for tunneling.

---

