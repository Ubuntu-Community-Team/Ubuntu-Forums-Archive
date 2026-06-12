---
title: "Can I get help creating launchers?"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by JohnBonne on 2011-06-02
When I  first got it, I was impressed by the interface of the DE of Ubuntu. There are things, though I first noticed because I have always used windows. I have Natty Narwhal installed on the USB drive I bought along side of Windows Vista. Cool beans, non? I right click, and I see a "Create Launchpad" toggle.

I would like to create a few applications using the create launchpad and have a couple of them I created, for a couple of games. Clear instructions where bleachbit's , System Monitor's and Character Map's  exe's are I can't find. I use several more files a lot, If someone would like to help me find them. I'll be back tonite. I love it but it tires me out.

---

### Post by Sam White on 2011-06-02
Sorry, are you creating launchers? In that case, can the command not just be "charmap" without quotes?

---

### Post by iansane on 2011-06-02
unity is the problem here. If you want to use unity you can click on applications and then type in the name of the app (if you know it, which is the problem with some of them). Also stinks that you don't get a right click menu on applications in unity. I got sick of unity and went back to classic ubuntu theme.

Here are the commands to use in the launchers:
character map : gucharmap
system monitor: gnome-system-monitor
bleachbit     : bleachbit
bleachbit as root : su-to-root -X -c bleachbit

That last one didn't work for me even though it's directly copied from the menu launcher. Might just change that to gksudo bleachbit to get it to work as root. And all of these should be left as "application".

Ways to find the launchers:
1. if you have classic theme menu just right click on the menu and choose edit menu, then find the app and view the properties of it to get the command for your launcher. Of course if you have classic menu you can just right click>add launcher to panel or desktop.

2.Apps that are not found in the menu can often be found in synaptic where you can right click and view properties>installed files to find out the name of the executable installed in bin or sbin. This will also show the full path from / (root).

3. google or the forum.

Often times the name of the executable is no where near the name of the application as it is called. ex. (gtk-recordmydesktop found in synaptic is the same program as "desktop recorder" in the software center and in the menu) It would be near impossible to just guess that but looking at bin, sbin, and synaptic usually helps.

---

### Post by iansane on 2011-06-02
> **Sam White said:**
> Sorry, are you creating launchers? In that case, can the command not just be "charmap" without quotes?

:lolflag: made my point about the names Sam White. charmap works too! :-)


It's gucharmap in the menu.

---

### Post by JohnBonne on 2011-06-02
> **iansane said:**
> unity is the problem here. If you want to use unity you can click on applications and then type in the name of the app (if you know it, which is the problem with some of them). Also stinks that you don't get a right click menu on applications in unity. I got sick of unity and went back to classic ubuntu theme.

Here are the commands to use in the launchers:
character map : gucharmap
system monitor: gnome-system-monitor
bleachbit     : bleachbit
bleachbit as root : su-to-root -X -c bleachbit

That last one didn't work for me even though it's directly copied from the menu launcher. Might just change that to gksudo bleachbit to get it to work as root. And all of these should be left as "application".

Ways to find the launchers:
1. if you have classic theme menu just right click on the menu and choose edit menu, then find the app and view the properties of it to get the command for your launcher. Of course if you have classic menu you can just right click>add launcher to panel or desktop.

2.Apps that are not found in the menu can often be found in synaptic where you can right click and view properties>installed files to find out the name of the executable installed in bin or sbin. This will also show the full path from / (root).

3. google or the forum.

Often times the name of the executable is no where near the name of the application as it is called. ex. (gtk-recordmydesktop found in synaptic is the same program as "desktop recorder" in the software center and in the menu) It would be near impossible to just guess that but looking at bin, sbin, and synaptic usually helps.

Synaptic doesn't open. Is there a reason for this? (i click on it and nothing happens!)

Thanks for the other app's true names.

---

### Post by iansane on 2011-06-02
hmmm... Not sure why synaptic would not open. Maybe a natty bug or a unity bug?

Try opening it through terminal which is in applications.

```
sudo synaptic
```

Sometimes running it from a terminal gives more hints of what's wrong like error messages that show up in the terminal.

---

### Post by JohnBonne on 2011-06-02
> **iansane said:**
> hmmm... Not sure why synaptic would not open. Maybe a natty bug or a unity bug?

Try opening it through terminal which is in applications.

```
sudo synaptic
```Sometimes running it from a terminal gives more hints of what's wrong like error messages that show up in the terminal.

Everything is OK now. I switched over to classic and typed ```
synaptic
``` into terminal. It opened without adm. permissions. 

I tried to install all it's packages on a long shot and still I couldn't open it with Control Center and still no. So I reinstalled it and presto! 

Since this is a minor problem, no reason to yell about it. I had it, it vanished and now it's back. Good thing, because It shows Ubuntu to be powerful and extendable.

Regards and much love,
John

---

### Post by JohnBonne on 2011-06-02
Before I close. There is the command line in the System Monitor under Processes; If you can get the program to start.

---

### Post by iansane on 2011-06-02
> **JohnBonne said:**
> Before I close. There is the command line in the System Monitor under Processes; If you can get the program to start.

Opened system monitor, went to edit>preferences under process tab list at bottom has command line unchecked. checked it and now shows the command line in the main processes tab.

Is that what your talking about? I never really used system monitor. I use htop to see the processes in the terminal and it shows the command line column by default but I see that system monitor is much more pleasing to the eye :-)

---

### Post by JohnBonne on 2011-06-03
> **iansane said:**
> Opened system monitor, went to edit>preferences under process tab list at bottom has command line unchecked. checked it and now shows the command line in the main processes tab.

Is that what your talking about? I never really used system monitor. I use htop to see the processes in the terminal and it shows the command line column by default but I see that system monitor is much more pleasing to the eye :-)

Yeah. when I closed the browser the system monitor was opened to system monitor. I know there are better, more technlogical ways. I am looking for 'em. I have been using other than Windows for about a month. Windows o/s  is so easy it has made me lazy.

But if you open sys monitor the command line for your various programs is shown. Not a bad method.

---

