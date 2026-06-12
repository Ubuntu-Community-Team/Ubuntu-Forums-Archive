---
title: "Connecting remote desktop..!!"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by vamsi_spr on 2010-12-26
1.)hi guys , could anyone please tell me the procedure on how to connect to my desktop ( windows7 installed ) through ubuntu ??

2.) Are there any ctrl+alt+del functionality equivalent function keys in linux ??

---

### Post by HermanAB on 2010-12-26
Howdy,

Use rdesktop:
$ rdesktop ipaddressofwin7machine

---

### Post by karthick87 on 2010-12-26
**Install Team viewer:**
  For Ubuntu,you can download teamviewer [here]("http://www.teamviewer.com/download/teamviewer_linux.deb"). Once downloading is completed, you can install it easily by double  clicking the file.After installation you can find team viwer under the  Internet Menu.
  **Open the Team Viwer:**
  Applications -- >>Internet -->> Team Viwer
  [IMG]http://i.imgur.com/eWwZs.png[/IMG]
  Before establishing the remote desktop connection,you must know the  ID and Password of the remote system which is running Team Viwer.After  getting the ID and Password from your partner.Enter the ID and click  connect to partner, with in few seconds it will show a window prompting   for a password.Enter the password which you got from your partner and  click ok.Now you are connected to remote sytem.

---

### Post by vamsi_spr on 2010-12-26
Cant i do it through remote desktop viewer which comes with ubuntu ??? ...And can anyone answer me my second question ??

---

### Post by spiky001 on 2010-12-26
I you use Ctrl+Alt+del it will give yo the shutdown dialog box is this what you are looking for, If you want to kill a process open  terminal type ```
top
```

---

### Post by davidmohammed on 2010-12-26
> **vamsi_spr said:**
> Cant i do it through remote desktop viewer which comes with ubuntu ??? 

not by default.  You might be aware that the next version of ubuntu - natty - will bring a new terminal server client called [remmina]("http://remmina.sourceforge.net/downloads.shtml").  Give it a shot.  It works very well for me.

---

### Post by spiky001 on 2010-12-26
Also if you go to Admininstration/System/System monitor.
What is it you want to do with remote desktop?

---

### Post by fatal_ERROR777 on 2010-12-26
You can use hamachi to control your desktop remotely.
[https://secure.logmein.com/US/labs/](https://secure.logmein.com/US/labs/)  - Linux command-line version
[http://www.haguichi.net/download/](http://www.haguichi.net/download/)    - graphical interface for hamachi. 
Unfortunately, linux vesion of hamachi doesn't have a chatting option. You can use "people nearby" option in Empathy or bonjour protocol in Pidgin.

Fatal_Error

---

### Post by vamsi_spr on 2010-12-26
can't we use any of the shortcut keys to end or kill processes ??

---

### Post by QLee on 2010-12-26
[QUOTE=vamsi_spr]can't we use any of the shortcut keys to end or kill processes ??[/QUOTE]

What "shortcut keys" did you use to end or kill processes in Windows.

Did you have a look at system monitor as spiky001 suggested, for example, the processes tab?


[Edit] Addition: It could also be done from the command line in a terminal or console too if you want that approach.

---

### Post by vamsi_spr on 2010-12-26
> **QLee said:**
> What "shortcut keys" did you use to end or kill processes in Windows.

Did you have a look at system monitor as spiky001 suggested, for example, the processes tab?


[Edit] Addition: It could also be done from the command line in a terminal or console too if you want that approach.

yes , checked it out , i meant ctrl+alt+del kind of functionality ,so that i could open 'system monitor' window when i need to kill a process through the shortcut keys !!

---

### Post by QLee on 2010-12-26
> **vamsi_spr said:**
> yes , checked it out , i meant ctrl+alt+del kind of functionality ,so that i could open 'system monitor' window when i need to kill a process through the shortcut keys !!

You could create a launcher for system monitor on the panel, or on your desktop or you could program your own choice of keys to launch system monitor, lots of options in Ubuntu. In Ubuntu we like the "three finger salute" to initiate a shutdown sequence. There are a lot of differences between Windows and Ubuntu some of them make more sense when you have more experience.

As mentioned you could even use the command line, that's the way I like to do it.

If you use the command, ps aux, in a terminal window you will see a listing of active processes (strictly speaking, a snapshot of the processes running at the time the command is entered). From that you could identify the pid (process ID) and use the command, kill (the number of the process) to kill the process if it's your user's process or prepend sudo if it is root's process.

That is a brief explanation, for more info, enter the command, man ps, in a terminal window to read the manual page for the command, ps. It will be a lengthy manual page to read and study.


You are probably fairly new at this so maybe this might help.

Some people from the Ubuntu community have put in quite a bit of effort to produce this manual as an easy for a beginner to understand step-by-step, with pictures, for reference to common tasks.
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)


[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Philosophy](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Philosophy)
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by CharlesA on 2010-12-26
+1 to the launcher idea.

I tend to use htop if I don't want to use ps aux and grep.

---

### Post by vamsi_spr on 2010-12-26
Hey can't i access audio files using team viewer ?? ...

---

