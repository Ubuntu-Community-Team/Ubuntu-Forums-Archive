---
title: "Need help installing basic games"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by Giomeister on 2010-11-30
I have Grim Fandango and World of Warcraft.

How do i install these through Wine. I have totally cleaned my computer from any MS products. I do not want to have to revert to the dark side. 

Please help.

I am not able to mount or figure it out. I used to use ISO buster and Daemon tools. 

How do i get this up and running?

---

### Post by I'mGeorge on 2010-11-30
in linux you can mount an iso image with the command 

```

cd /path_to_the_ISO_file
sudo mount -o loop ISO_file /media/cdrom

```

this way your iso file would be mounted in your cdrom usual mounting point. After that just install wine using synaptic package manager or the command apt-get install wine , and the exe file should be automatically executed by wine when you double click on it. If it's not than right click on the exe file select open with and than choose wine from the programs available.

And that's about it.

---

### Post by Perfect Storm on 2010-11-30
> I am not able to mount or figure it out. I used to use ISO buster and Daemon tools. 

How do i get this up and running?

Get furiusisomount from ubuntu repository.


regarding the game I would recommend you take a look and search in our wine forum: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
You'll find all the info you need there.

---

### Post by Giomeister on 2010-12-02
I am still stuck at square one. WOW is playing intro then i get an error and it crashes. Thinking maybe virtual memory was changed when i solo-ed this.

Ubuntu is the only OS i am using now.
the icon is still on top fo the desktop, and it launches intro movie. Then crashes.

4.02 i think.......................



)

Exe:      C:\World of Warcraft\Wow.exe
Time:     Dec  2, 2010  8:33:32.312 PM
User:     jdg
Computer: jdg-F6A
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:6828D0AA

The instruction at "0x6828D0AA" referenced memory at "0x0000000C".
The memory could not be "read".

---

