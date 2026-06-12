---
title: "Ipod-Convenience troubles - SSH: IPDADRESS: name or service not known"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by Dontgetit on 2008-03-02
Hello! I have searched the forums (and Google) and hope I'm posting in the right place. I'm having lots of trouble with ssh and the ipod-convenience script all of a sudden.

I have it running on two computers with Gutsy. It was working on my laptop last night and then all of a sudden, when I pop a terminal and write "iphone-mount" I get the following error.

ssh: IPDADDRESS: Name or service not known

I have uninstalled and reinstalled ipod-convenience many times. I know the issue isn't with my iphone because i'm able to mount it on my other computer.

PLEASE HELP! I'm really at a loss and am desperate for guidance.

Thanks so much!
__________________

---

### Post by exekias on 2008-03-02
i have the same problem on my itouch but sometimes if i wait for 10 minutes it turns around and says "timed out" then asks for my password.

i have

amorok
gtkpod 9.12
libgpod 3
ipod convenienc

anything else i need?? i use filiezilla to normally ssh

please reply

---

### Post by exekias on 2008-03-02
okay now i just upgraded ipod convenience and it now just says
ssh: : Name or service not known

---

### Post by BGreet on 2008-03-03
****assuming you're using an ipod w/ either 1.1.4 or 1.1.3 firmware****

sudo gedit /usr/share/ipod-convenience/mount-umount

go to the line where it says
#Figure out our username
ssh root@$IPDADDRESS test -d /var/mobile

and make it this:
#Figure out our username
#ssh root@$IPDADDRESS test -d /var/mobile

then under the line starting with:
#Mount our Music Directory
comment out (put a # in front of) every line except for
sshfs root@$IPADDRESS:/var/mobile/Media $MOUNTPOINT/ -o workaround=rename

save file and mount

---

### Post by exekias on 2008-03-03
i tried that but its read only and apparently i dotn have the permission to alter it! im administrator and the only user what do i do now, cheers

---

### Post by ntetreau on 2008-03-04
I can confirm this is a bug in the latest ipod-convenience ([bug 198139]("https://bugs.launchpad.net/ipod-convenience/+bug/198139"))

I found a workaround i think.  In iphone-mount :

```

sudo gedit /usr/bin/iphone-mount

```

Change line 66 from:

```

    if ssh root@192.168.6.136 test -d /var/mobile; then

```

to

```

    if ssh root@$IPADDRESS test -d /var/mobile; then

```

I still get the "ssh: : Name or service not known" message but it mounts fine for me

By the way, you guys might want to take the habit of posting your ipod touch or iphone problems in the following [thread]("http://ubuntuforums.org/showthread.php?p=4450518#post4450518") as most users are subscribed to it and can help faster!

---

### Post by xjgnsdof on 2008-03-08
emones@Gavel1:~$ ipod-touch-mount
ssh: : Name or service not known
root@192.168.1.7's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
root@192.168.1.7's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

What's going on, there?

---

### Post by ToohTaah on 2008-03-09
@elgilicious
Make sure your ipod (or iphone) is not mounted to your PC (either turn off openssh or wifi on your device). Then, check the mount point and see if it is empty. 

HTH

---

### Post by xjgnsdof on 2008-03-09
When I turn them off, I get the following:

iPod is not responding to pings at 192.168.1.7.
Please set the environment variable IGNOREPING if you want to ignore this.

---

### Post by xjgnsdof on 2008-03-12
I have finally synched my iPod Touch in gtkpod. It's really quite simple, but the wiki instructions aren't very well written. As such, I think I owe it to the community to clarify them, at least for my iPod Touch.

INSTRUCTIONS FOR MOUNTING JAILBROKEN 1.1.3 IPOD TOUCH
1. Follow the instructions at the[ official wiki page]("https://help.ubuntu.com/community/PortableDevices/iPhone#head-2324e37d080ca00c9738c8653562c84872ab4a72"), stopping right after you complete step 4.

2. Input the following: ```
sudo gedit /usr/bin/iphone-mount
```

3. Find the following section of code, roughly around line 66
```
#Mount our Music Directory
#work around if its 1.1.3+
if ssh root@IPADDRESS test -d /var/mobile; then
```

where"IPADDRESS" = an actual IP address
4. Change this IP address to "$IPADDRESS" without the quotes.
5. Make sure that the /media/ipod/ directory is completely empty, whether it be through Nautilus or in the command line
6. Run the following to mount your iPod Touch: ```
ipod-touch-mount
```

I feel kind of weird going from having no clue how to mount my iPod Touch to claiming that I can write better instructions, but such is learning. Let me know if you can finally mount and sync your jailbroken 1.1.3 iPod Touches.

---

### Post by Behrend on 2008-07-16
everytime i run ipod-touch-mount
it asks me 2 time for my ipod-touch password
and then it gives me an error:
the xterm says: ipod-touch-mount
root@192.168.178.29's password:
root@192.168.178.29's password:
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
 and amarok says (after asking me 2 times for the password)
Media Device: no mounted ipod found
whats wrong? please help me

---

