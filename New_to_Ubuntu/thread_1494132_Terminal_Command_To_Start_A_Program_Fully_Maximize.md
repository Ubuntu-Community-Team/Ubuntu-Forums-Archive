---
title: "Terminal Command To Start A Program Fully Maximized"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-26
Title says it all :)

if i type this command in terminal, opera starts restored.
```
opera
```

i want to start it fully maximized.

---

### Post by TheStroj on 2010-05-26
use 'opera --help' to see all the available commands for this program. I don't know if there is command to maximize, but give it a try and you'll see.

---

### Post by kerry_s on 2010-05-26
type: **opera --help**
in a terminal & see if theres a switch for that.
otherwise you'll have to do some kind of script, with something like wmctrl.

---

### Post by SKhan on 2010-05-26
> **TheStroj said:**
> use 'opera --help' to see all the available commands for this program. I don't know if there is command to maximize, but give it a try and you'll see.

opera help says nothing regarding this issue. It's a closed source program and is not included in ubuntu repository.
and my question is not limited to just opera. i may use maximize command for other programs as well.

---

### Post by SKhan on 2010-05-26
here's opera --help output. i can't get any help from this help output.

> A url is by default opened in a new tab

 -widget <file>                 open widget
 -widgetmanager                 open widget manager
 -newwindow                     open url in new window
 -newtab                        open url in new tab (default behavior)
 -newprivatetab                 open url in new private tab
 -activetab                     open url in current tab
 -backgroundtab                 open url in background tab
 -fullscreen                    start in full screen state
 -geometry <geometry>           set geometry of toplevel window
 -remote <command>              send command to another Opera window
 -window <window id>            id of remote Opera window
 -windowname <window name>      symbolic name of remote Opera window
 -noraise                       do not raise Opera window when sending a remote command
 -nosession                     do not use saved sessions or homepage
 -nomail                        start Opera without internal e-mail client
 -noargb                        do not use an ARBG (32-bit) visual
 -nolirc                        do not use LIRC (infra red control)
 -nowin                         do not use saved sessions or homepage
 -display <display name>        set the X display
 -version                       show version data
 -full-version                  show version data and build details
 -pd <path>                     location of alternative Opera preferences folder
 -sd <path>                     location of alternative Opera shared resource folder
 -bd <path>                     location of version-specific binaries folder
 -mail                          starts displaying unread mails
 -help                          displays command line help
 -?                             displays command line help
 -kioskhelp                     displays kiosk mode command line help
 -debughelp                     displays available debug options
 -lirchelp                      extra options for LIRC (infra red control)
 -urllist <filepath>            load each line in the given page in an automated run
 -urllistloadtimeout <seconds>  timeout for each page specified with 'urllist' argument

Remote commands:

 openURL()                      open "Go to" dialog box prompting for input
 openURL(url[,noraise])         open url in active window
 openURL(url[,dest][,noraise])  open url in destination <W|T|B>
 openFile([dest])               open file selector in destination <W|T>
 openM2([dest][,noraise])       open M2 list view in destination <W>
 openComposer([dest][,noraise]) open M2 composer in destination <W>
 addBookmark(url)               add url to bookmark list
 raise()                        raises the opera window
 lower()                        lowers the opera window

 [dest] Replace W: 'new-window', T: 'new-tab', B: 'background-tab'
 [noraise] prevents target window to be raised

 A standalone url argument or '-newwindow', '-newtab', '-backgroundtab'
 or '-nowin' will disable '-remote' commands

Notes:

 * <geometry> format is: WIDTHxHEIGHT+XOFF+YOFF
 * '-window' and '-windowname' work for '-remote' and '-newwindow' commands
 * '-window' accepts a hexadecimal or a decimal argument
 * '-fullscreen' works when a new browser is launched
 * '-nowin' disables any url argument
 * '-windowname' will override '-newwindow' if a named window is located

---

### Post by TheStroj on 2010-05-26
Read the output:
```
-fullscreen start in full screen state
```

might be what you are looking for

---

### Post by SKhan on 2010-05-26
> **TheStroj said:**
> Read the output:
```
-fullscreen start in full screen state
```

might be what you are looking for

this command starts application in fullscreen. I didn't mean fullscreen. I meant maximzed.

---

### Post by kerry_s on 2010-05-26
the "-geometry" switch might work. just put your screen size & it should fill.

example: opera -geometry 1024x768

---

### Post by TheStroj on 2010-05-26
> **SKhan said:**
> this command starts application in fullscreen. I didn't mean fullscreen. I meant maximzed.

I downloaded Opera just because of you to try this out. 

Opera remembers the last configuration which means: If you closed it when it wasn't maximized it will open not-maximized. 
If you close it maximized, it will open maximized.

If you have access to it, open it, maximize it, close it, reopen it. Should work only with command 'opera'. 

About that, when you said you might want to use 'maximize' command for other programs - every program can have it's own command for this.

---

### Post by SKhan on 2010-05-26
> **TheStroj said:**
> I downloaded Opera just because of you to try this out. 

Opera remembers the last configuration which means: If you closed it when it wasn't maximized it will open not-maximized. 
If you close it maximized, it will open maximized.

If you have access to it, open it, maximize it, close it, reopen it. Should work only with command 'opera'. 

About that, when you said you might want to use 'maximize' command for other programs - every program can have it's own command for this.

oh so good of you. keep it installed if you like it. I always prefer open source programs. Opera is the only exception.

i always use it maximzed, hence always close it maximzed. i have access to opera and i can open it from panel icon or from applications menu.
but i am using easystroke mouse gestures to launch opera and some other applications i use frequently. and when i launch opera using easystroke it sometimes starts maximzed and sometimes restored.
easystroke understands terminal commands. so it will be of great use, if there's a common command to start all applications in maximzed mode.
such as
opera maximized
firefox maximized.
vlc maximzed.
and so on.

---

### Post by SKhan on 2010-05-26
> **kerry_s said:**
> the "-geometry" switch might work. just put your screen size & it should fill.

example: opera -geometry 1024x768

no it didn't work.

---

### Post by SKhan on 2010-05-27
what do i do guys? ](*,)

---

### Post by aninaiian on 2010-05-27
Okay, I believe this will work granted it's not the ideal solution.  First, install wmctrl via
```
sudo apt-get install wmctrl
```
Then create a text file with the contents below
```
#!/bin/bash

PID1=`wmctrl -l | tail -n 1 | awk '{print $1}'`
$1&
PID2=`wmctrl -l | tail -n 1 | awk '{print $1}'`
COUNT=0

while (("$PID2"=="$PID1" && $COUNT<=10))
do
  sleep 1
  PID2=`wmctrl -l  | tail -n 1 | awk '{print $1}'`
  COUNT=$COUNT+1
done
  #echo $PID2
  if (( $COUNT<=10 )) ; then
    wmctrl -i -r $PID2 -b add,maximized_horz,maximized_vert
  fi
```

Give the file execute permissions either by right clicking the file, clicking "Properties", going to the "Permissions" tab, and checking the "Allow executing the file as a program" box.  Or doing a
```
chmod u+x WHATEVERTHEFILENAMEIS
```
and it should be ready to try out on the terminal.
To use it just enter
```
PATHTOEXECUTABLE APPTOBEMAXIMIZED
```

Like I mentioned before it's not ideal and a bit of a dirty hack...  Basically, the script launches the app and checks every second for 10 seconds for the window manager to say that there's an newer window than the newest window at the time before the apps launch.  If there is a newer window it maximizes the newest window and the script ends or if no newer window is spawned within the 10 seconds it quits and just launches the app.  What this means is if another window is created around the same time as the one you're to maximize, that window may maximize instead of the one you wanted.

---

### Post by SKhan on 2010-05-27
aninaiian thanks. let me try it. i will inform you when i am done.

---

### Post by mufti on 2010-06-02
@aninaiian 
thx bro, couldn't start opera maximized but your solution helped  :guitar:

---

### Post by SKhan on 2010-06-07
> **aninaiian said:**
> Okay, I believe this will work granted it's not the ideal solution.  First, install wmctrl via
```
sudo apt-get install wmctrl
```
Then create a text file with the contents below
```
#!/bin/bash

PID1=`wmctrl -l | tail -n 1 | awk '{print $1}'`
$1&
PID2=`wmctrl -l | tail -n 1 | awk '{print $1}'`
COUNT=0

while (("$PID2"=="$PID1" && $COUNT<=10))
do
  sleep 1
  PID2=`wmctrl -l  | tail -n 1 | awk '{print $1}'`
  COUNT=$COUNT+1
done
  #echo $PID2
  if (( $COUNT<=10 )) ; then
    wmctrl -i -r $PID2 -b add,maximized_horz,maximized_vert
  fi
```

Give the file execute permissions either by right clicking the file, clicking "Properties", going to the "Permissions" tab, and checking the "Allow executing the file as a program" box.  Or doing a
```
chmod u+x WHATEVERTHEFILENAMEIS
```
and it should be ready to try out on the terminal.
To use it just enter
```
PATHTOEXECUTABLE APPTOBEMAXIMIZED
```

Like I mentioned before it's not ideal and a bit of a dirty hack...  Basically, the script launches the app and checks every second for 10 seconds for the window manager to say that there's an newer window than the newest window at the time before the apps launch.  If there is a newer window it maximizes the newest window and the script ends or if no newer window is spawned within the 10 seconds it quits and just launches the app.  What this means is if another window is created around the same time as the one you're to maximize, that window may maximize instead of the one you wanted.

Thanks man. It worked and completely solved my problem.

---

### Post by b0b138 on 2010-06-07
[http://ubuntuforums.org/showthread.php?t=600003](http://ubuntuforums.org/showthread.php?t=600003)   read the last post :)

---

### Post by SKhan on 2010-06-10
> **b0b138 said:**
> [http://ubuntuforums.org/showthread.php?t=600003](http://ubuntuforums.org/showthread.php?t=600003)   read the last post :)

Thanks man. it worked.

---

### Post by SynonM on 2012-01-30
Does anybody have a simpler way to do this with the terminal itself?;)

I've been searching, but I don't want to start randomly changing Xserver settings or the terminal file. Simple and fairly easy edit to a terminal config file or something.

So far I have a short-cut key which starts terminal maximized but I have to hit F11 to have it fully maximized.


```
terminal --maximized
```

I don't mind it, but a quick fix would be nice while keeping the window manager installed. 

I don't really want to download additional software or run a script.

Just a file edit.

---

### Post by SynonM on 2012-01-30
:) Solved my own problem. Changed the terminal settings so that the borders don't start with Terminal.

Fully maximized. Hope that might help someone.:popcorn:

---

### Post by calande on 2012-07-27
So complicated just to start a program maximized... :rolleyes:

---

