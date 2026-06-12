---
title: "GDM didn't work"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by toloykhan on 2010-10-18
hello there, 
I have a really critical case here .... I was trying to login without GDM and found post in this forum and follow .. the steps was >>
1/ open terminal and the edit the file /etc/X11/default-display-manager  which contain the line
/user/sbin/gdm 
2/ reboot 
I did the steps as they shown but when I reboot the computer didn't log me in either with GDM or else 

then I tried to fix it by login with failesave mode ... it did work fine for me but when I tried to start gdm again got the following message

root@toloykhan-desktop:/home/toloykhan# gdm

** (gdm-binary:12394): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:12394): WARNING **: Could not acquire name; bailing out


for knowlage I have install compiz if that matter
help me please I need to work ..

thanks in advance ....

---

### Post by toloykhan on 2010-10-18
I just found the solution... it is simple .. I just remove the GDM
aptitude purge gdm
then 
aptitude install gdm 
then remove the nvidia driver and reinstall it from System> Administration > Hardware Driver
then I reboot and every thing work fine...

---

### Post by cavh on 2010-10-18
[EDIT - JUST SAW THAT YOU HAVE FIXED IT, WELL DONE]

Assuming you can log in again in failsafe mode, you need to edit /usr/sbin/gdm again, changing back the values to the ones you had before. This is the content of the file on my Lucid (10.04) machine:

```
clive@clive-home:~$ cat /usr/sbin/gdm
#!/bin/sh
#
# A script so that
#    1) we read the standard system env vars
#    2) syadmins/integrators can add their own private options etc...

test -f /etc/profile && . /etc/profile

# Make sure LANG is set
#
if [ -z "$LANG" ]
then
  if [ -f /etc/sysconfig/language ]
  then
    LANG=`. /etc/sysconfig/language; echo $RC_LANG`
    export LANG
  fi
fi

exec /usr/sbin/gdm-binary "$@"
```

Once you are logged in, type the following command to recreate the file:

```
sudo nano /usr/sbin/gdm
```

Then type out the text I listed above, and save the file, then reboot. If you need some help on the nano text editor commands, see 

[http://www.nano-editor.org/dist/v2.2/nano.html]("http://www.nano-editor.org/dist/v2.2/nano.html")

---

### Post by toloykhan on 2010-10-20
cavh... , 
thank you very much for your replay ... I really don't know v.much in this technical issues so that I had fall in this problem .. as I said I just solve this by entering to the system using failsafe mode and then deactivate the VGA adapter and reactive it then I reboot and set the resolution and every thing goes well .. here is my result for 
cat /usr/sbin/gdm

#!/bin/sh
#
# A script so that
#    1) we read the standard system env vars
#    2) syadmins/integrators can add their own private options etc...

test -f /etc/profile && . /etc/profile

# Make sure LANG is set
#
if [ -z "$LANG" ]
then
  if [ -f /etc/sysconfig/language ]
  then
    LANG=`. /etc/sysconfig/language; echo $RC_LANG`
    export LANG
  fi
fi

exec /usr/sbin/gdm-binary "$@"

thank you again

---

