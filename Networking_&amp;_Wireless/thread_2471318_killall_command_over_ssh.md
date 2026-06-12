---
title: "killall command over ssh"
date: 2022-01-26
forum: Networking &amp; Wireless
---

### Post by buill on 2022-01-26
hi if i run killall firefox in terminal it kills all instances of firefox but if i run killall firefox via ssh from another machine it does nothing so how do you kill a proccess over ssh? sorry if this is in wrong section thanks for any help.


sry an update im working on a debian machine which the command works fine on but remote ubuntu even when done manually at machine results in no proccess found. is there a package i have to install?


further update if i launch kodi from a terminal killall kodi kills kodi but if i just launch it as app killall doesint work wtf ? anyone know why this is? thanks

---

### Post by The Cog on 2022-01-26
Two things come to mind:
What's the name of the running process? I think I remember the running firefox process being called firefox-bin. Try listing all processes with firefox in their name with this command might show something useful. At least if might give you a process id to kill:
```
ps -ef | grep firefox
```
Secondly, are you logging in as the same user? You can't kill other user's processes unless you use sudo.

---

### Post by SeijiSensei on 2022-01-26
If I have used ssh to connect to another machine, then of course any actions I take will be limited to that machine. So if I issue a "killall firefox", or to avoid permission problems, "sudo killall firefox", it should kill all the firefox instances on the remote machine.  You would see nothing at your end since the process killing happened on the other machine.

Now if you were to log in to the remote using the "-X" option to ssh, then running the command "firefox &" on the remote machine will make an instance of the program appear on your screen.  If you were then to "killall firefox" on the remote, the running window on your machine should disappear.

---

### Post by TheFu on 2022-01-27
Firefox is an odd bird.  They decided that starting it on a remote system would, by default, start it on the local system years ago.  You can disable this with a CLI startup option.  I think the option is in the manpage.  So ... when you try to kill firefox on a remote machine, it isn't actually running there.  It has been running on your local workstation.   That's my guess.

Here's the manpage item:
```
       -no-remote
              Don't connect to any other running  instances  of  firefox.  Use
              this  if  you want to run firefox in an entirely new process. By
              default, firefox will delegate a command to an  already  running
              instance.
```

So, when you run firefox over a remote X11 connection, be certain to include that CLI option too.
```
$ ssh -X username@remote firefox -no-remote  $@ & 
```
is probably what you want.  Best to have ssh-keys setup between the client and server too.
And if you add in a firejail, there are some other settings required and --ignore=seccomp is needed.

When firefox is installed as a snap package, I bet all these things will be broken. At a minimum, we'll need to manually setup the ~/.Xauthority inside the snap package "current" directory as a symlink.

---

### Post by buill on 2022-01-27
thanks for replys i think the prob with firefox is im not running esr so its an executable in my home folder however the kodi one has my head wrecked as the shortcut command run as app wont kill but if run in terminal is selected it works. another problem is im not running it from terminal im building an automation app to close 1 app and open another but im am defo logging in and commands like 
[COLOR=#067d17]"killall mate-terminal[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"

works but not for kodi and although i get connected from turning on bluetooth and connecting a ps4 controller the controller wont connect head is wrecked but need to get working as to switch between kodi and pcsx2 or back again requires going into my kitcen and climbing on counters
[/COLOR]

---

### Post by TheFu on 2022-01-27
If you start the application, save the PID for that application somewhere, so you don't have to use the shotgun 'killall'.  You can kill the exact PID instead.  
Also, when running applications in a script, it is best to specify the exact location to the program, not trusting whatever the "PATH" has.  When killing, if you don't know the PID, using a search of the process table to get the PID for the exact instance to be killed is how I do it. If the results contain more than a single result in the list, what does that mean?  Could be expected or it could be bad.

I have a kodi-restart script that I can call from a number of clients.  The script sits on the kodi systems here (there are 3).

---

### Post by buill on 2022-01-29
i got it working ny launching kodi from terminal not as application must be down to users or something however my problem with connecting bluetooth ps4 controllers persists 
i am connecting with commands
bluetoothctl devices
bluetoothctl discoverable on
bluetoothctl pair 98:B6:E9:5C:25:E4
bluetoothctl connect 98:B6:E9:5C:25:E4
bluetoothctl trust 98:B6:E9:5C:25:E4

which gives output

Device 98:B6:E9:5C:25:E4 Wireless Controller
Changing discoverable on succeeded
Attempting to pair with 98:B6:E9:5C:25:E4
Failed to pair: org.bluez.Error.AlreadyExists
Attempting to connect to 98:B6:E9:5C:25:E4
[CHG] Device 98:B6:E9:5C:25:E4 Connected: yes
Failed to connect: org.bluez.Error.Failed
Changing 98:B6:E9:5C:25:E4 trust succeeded

it seems to connect but then drop connection however it does work once in a blue moon (bluetooth joke) but it always works from devices gui app anyone have any suggeestion on what could be the problem or a possible solution? thanks again for replys and help

---

### Post by buill on 2022-01-29
k i can get it to work if i remove device from gui app scann with gui app then run commands in ternimal and it connects but wont reconnect after dissconnecting its like something need to be reset

---

### Post by buill on 2022-01-29
k so if i remove device from list scan with gui app then run commands

bluetoothctl devices
bluetoothctl discoverable on
bluetoothctl pair 98:B6:E9:5C:25:E4
bluetoothctl trust 98:B6:E9:5C:25:E4
bluetoothctl connect 98:B6:E9:5C:25:E4

it works but if i disconnect then i cant reconnect unless i repeat the removal from list and repeat something needs to be reset but i need all this to work from commands i will post fix once found

---

### Post by buill on 2022-01-29
started new thread for this prob thanks for help

[https://ubuntuforums.org/showthread.php?t=2471409&p=14078222#post14078222](https://ubuntuforums.org/showthread.php?t=2471409&p=14078222#post14078222)

---

