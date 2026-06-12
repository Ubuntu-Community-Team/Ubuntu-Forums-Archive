---
title: "start-up program"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by pua06 on 2011-06-21
salmo allikm warhmat allah wa brakato

i want to know how to do autostart programmes  in xfce?
i know GUI but want how in terminal with commend line

thanks

---

### Post by kerry_s on 2011-06-21
Just type the name & enter 

You can type a few letters & press tab for auto complete

---

### Post by pua06 on 2011-06-21
> **kerry_s said:**
> Just type the name & enter 

You can type a few letters & press tab for auto complete

 thanks
i don't understand what you mean type name &enter?
where

---

### Post by jerrrys on 2011-06-21
just enter the "name of app" in terminal.

---

### Post by pua06 on 2011-06-21
i mean when pc login
 Autostart program from terminal

---

### Post by nzjethro on 2011-06-21
For example, to launch thunar file manager, you type

```
thunar
```

in your terminal, and hit enter.

To launch firefox (internet browser), type

```
firefox
```

then hit enter.

---

### Post by Enigmapond on 2011-06-21
That won't happen but you can add anything to start up in Preferences/Startup Applications. Just hit add and enter the command. When the system boots, that programme will come on.

---

### Post by nzjethro on 2011-06-21
Alright, to set up autostart programmes, go to Settings > Startup Applications > Autostart tab. Then click "Add" (it may be a plus sign depending which release you're on), then in "Command", either type the name of the programme (e.g. firefox), or else browse to where the progromme is located (probably /usr/bin/) and click on the file there that matches the name of the application you are trying to start. In "Name" write the name of the application. Then click OK, and make sure that the check box next to the programme has a tick in it.

Note: I'm using Xfce, so if you are using regular Ubuntu, it may be slightly different, but the basic process is the same.

---

### Post by pua06 on 2011-06-21
> **nzjethro said:**
> Alright, to set up autostart programmes, go to Settings > Startup Applications > Autostart tab. Then click "Add" (it may be a plus sign depending which release you're on), then in "Command", either type the name of the programme (e.g. firefox), or else browse to where the progromme is located (probably /usr/bin/) and click on the file there that matches the name of the application you are trying to start. In "Name" write the name of the application. Then click OK, and make sure that the check box next to the programme has a tick in it.

Note: I'm using Xfce, so if you are using regular Ubuntu, it may be slightly different, but the basic process is the same.


thanks i know how do with GUI but i want to do with commend line in terminal

---

### Post by jerrrys on 2011-06-21
how bout this

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Autostart_a_program_at_bootup](http://ubuntuguide.org/wiki/Ubuntu:Natty#Autostart_a_program_at_bootup)

---

### Post by nzjethro on 2011-06-21
Jerrys' solution looks good, else if you know where the .desktop file of the application is kept, you could use

```
sudo cp /path/to/application.desktop /etc/xdg/autostart/
```

---

### Post by pua06 on 2011-06-21
> **jerrrys said:**
> how bout this

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Autostart_a_program_at_bootup](http://ubuntuguide.org/wiki/Ubuntu:Natty#Autostart_a_program_at_bootup)

thanks for link have a lot of information

i tested it  and have 2 question
sudo ln -s /usr/bin/firefox ~/.config/autostart

 that i get i changed firefox to any wrong name program still output?????

> ln: creating symbolic link `/home/user/.config/autostart': File exists

2- ~  means in home directory when i try to find  /home/user/.config/autostart i can't find it?

---

### Post by pua06 on 2011-06-21
> **nzjethro said:**
> Jerrys' solution looks good, else if you know where the .desktop file of the application is kept, you could use

```
sudo cp /path/to/application.desktop /etc/xdg/autostart/
```

 thanks so much
 can tell me how search or where  application .desktop could be kept??
there is away to know ?

---

### Post by nzjethro on 2011-06-21
> **pua06 said:**
> thanks so much
 can tell me how search or where  application .desktop could be kept??


It will likely be in /usr/share/applications

Here is an example that I ran to get Firefox starting when Ubuntu starts up:

```
sudo cp /usr/share/applications/firefox.desktop /etc/xdg/autostart

```

For another application, replace firefox with the name of the application. To get the name of the application, run
```
cd /usr/share/applications
ls
```

Then find the name of your application, and replace *firefox.desktop* with *<your-application-name>.desktop*.

Hope this helps. :D

---

### Post by pua06 on 2011-06-22
> **nzjethro said:**
> It will likely be in /usr/share/applications

Here is an example that I ran to get Firefox starting when Ubuntu starts up:

```
sudo cp /usr/share/applications/firefox.desktop /etc/xdg/autostart

```For another application, replace firefox with the name of the application. To get the name of the application, run
```
cd /usr/share/applications
ls
```Then find the name of your application, and replace *firefox.desktop* with *<your-application-name>.desktop*.

Hope this helps. :D

thanks so much

the problem that i installed application and i don't know where could be?
when i run it ,i run with terminal not with GUI
so i need to know where  installed application could be kept? may this help me
thanks

---

### Post by nzjethro on 2011-06-23
You can use the **locate** command to find your .desktop file.

For example, to find firefox.desktop, use

```
locate firefox.desktop
```

It is possible that when you installed the application it wouldn't have created a desktop file. To create a desktop file, use the following template.

```
#!/usr/bin/env
 
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Name=<Name of application>
Icon=/file/path/to/icon/file.icon
Exec=/file/to/executable/file
```

This may be a little confusing, so if you have any issues, feel free to ask.

---

