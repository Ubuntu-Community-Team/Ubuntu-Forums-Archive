---
title: "Start x11vnc via Startup Applications"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by zolointo on 2010-07-05
Good afternoon,

I can get a VNC server up and running manually on my Ubuntu box, but I'm having a hard time getting it to start automatically.

I've added the x11vnc application to my list of apps via the Startup Applications panel. This starts up the x11vnc but presents the x11vnc Properties window, instead of auto-starting, meaning I have to click on "Accept Connections" and then Apply/OK to get things rolling.

I added the following flags to the startup command, but still no dice:
/usr/bin/x11vnc -accept -solid

Desired end-state:
- x11vnc launches when my profile logs in
- starts accepting connections immediately
- minimizes any of the GUI to a taskbar icon

Ideas?

-Matt

---

### Post by krunge on 2010-07-05
I think this cmdline in startup will do what you want:
```
/usr/bin/x11vnc -gui tray
```
If you want to add other options like "-solid" you can add them. 

If you don't want to have a gui (tray or otherwise) remove "-gui tray"

Be sure to NOT use or reference any x11vnc.desktop file: you should run x11vnc directly.  The x11vnc.desktop has the naive-user options to ask them if they want to accept connections.

Also be sure that neither vino nor krfb are running.

---

### Post by zolointo on 2010-07-05
Thanks, Krunge.

I managed to get it working like so:

1. Removed x11vnc from the Startup Applications panel
2. Edited .profile and added the following lines (in sequence)
[LIST]
[*]/usr/bin/x11vnc -gui tray -solid
[*]/usr/bin/x11vnc -R unlock
[*]/usr/bin/x11vnc -R solid
[*]/usr/bin/x11vnc -R zeroconf
[/LIST]

I'm guessing that the solid option is redundant, but I couldn't figure out any other way to perform the unlock without a mouse click.

---

### Post by krunge on 2010-07-05
x11vnc should not start in a locked state. Are you sure yours is? One needs to specify -deny_all to have it start in a locked state.

You didn't accidentally create a ~/.x11vncrc file did you?  If so get rid of it or read it carefully (I recommend the former.)

I don't think you need any of the -R's.  Put -solid and -zeroconf on the cmdline.

---

### Post by zolointo on 2010-07-05
Right. I did generate a .x11vncrc file through the Advanced... button on the gui.

Alterations:
1. Deleted .x11vncrc file
2. Deleted garbage -R lines in my .profile
3. Restarted computer
4. Logged in with my profile
5. ... problems

When I'm looking at the screen during login, all I see is a mini-VNC icon in the upper right hand corner, and it doesn't present the full desktop. Good thing is that I _can_ VNC into the machine, but it also only shows the mini-VNC icon and nothing else.

If I click on that icon, it presents the simple GUI. Clicking on OK only minimizes the simple GUI to the mini-VNC icon again... still no full desktop.:-s

re: Any ideas from here? I can get in through another profile and alter the .profile for mine to set things back to basics.

I'm glad that I'm posting this in the newb forum so that I don't have to justify my newb-ness.

---

### Post by krunge on 2010-07-05
You really put the x11vnc command in your ~/.profile file?  I don't think that is a good place for it.  It should either be in a User Desktop startup script (for when you log into your desktop session at the physical console) or in a System Desktop startup script (started by the system when the login greeter panel is launched.)

Are you sure vino and krfb are not running?  Type 'ps wwaux' or use 'top' to be sure.

(PS: I feel ~/.profile is a bad place for launching x11vnc because that could start up a new x11vnc EACH TIME you launch a terminal window or possibly other apps, i.e.. leading to a mess.)

---

