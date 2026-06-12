---
title: "Samba share, location does not exist error?"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by jm8254og on 2008-07-27
Hey, I just reinstalled Ubuntu 8.04 and I set up my shares.  I basically now have a Buffalo linkstation 320 with all my music on it.  I edited my fstab 
//192.168.2.15/share/music/joey    /media/music        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

That worked before when my share was on a old computer I was using as a file server.  Now it mounts at startup and I can see the files and add to the share and copy from the share but if I click on a music file it launches totem and an error message says "ERROR HAS OCCURRED" location not found.  Same thing with any other player. 

There has been a problem with linkstations and permissions I think but that was in Vista and there is no permission error here.  I just wondered where to start?

Thank you

---

### Post by dmizer on 2008-07-28
Does the Linkstation support cifs?  I'm not sure if it does or not, and a quick search on Buffalo Technology's website didn't help.

edit:
You say that this fstab line did work before, so I will assume that the Linkstation does indeed support cifs.

With that in mind, you should try enabling wins support as outlined under the "Prework" section of this howto: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by jm8254og on 2008-07-28
Ok I will try that but is wins just for DNS hostname resolution?  I have a static IP on my linkstation.  I may be be totally wrong on that just want to learn and don't get me wrong I am going to try that and I appreciate your help a lot.  Oh and no I never got the linkstation working with an Ubuntu client so I don't have any confirmation that it support cifs.  If you think that maybe the issue I will search for that and thats exactly what I needed... a starting place.  Thank you.

---

### Post by dmizer on 2008-07-28
> **jm8254og said:**
> Ok I will try that but is wins just for DNS hostname resolution?  I have a static IP on my linkstation.  I may be be totally wrong on that just want to learn and don't get me wrong I am going to try that and I appreciate your help a lot.  Oh and no I never got the linkstation working with an Ubuntu client so I don't have any confirmation that it support cifs.  If you think that maybe the issue I will search for that and thats exactly what I needed... a starting place.  Thank you.

Okay, for some reason, CIFS seems to need wins in order to find the server.  I'm not sure why this is the case, but it has fixed many problems like what you describe.

There is a link to a thread in my howto for compiling smbfs.  You will need that if your Linkstation does not support CIFS.

---

### Post by jm8254og on 2008-07-28
Ok got a question.  If cifs is the problem what are my alternatives and how can I implement them?  I just followed a tutorial on editing my fstab but if I used a different approach what would be the parameters for a folder without password protection?

---

### Post by dmizer on 2008-07-28
> **jm8254og said:**
> Ok got a question.  If cifs is the problem what are my alternatives and how can I implement them?  I just followed a tutorial on editing my fstab but if I used a different approach what would be the parameters for a folder without password protection?

The tutorial I linked above (and also appears in my signature) gives examble fstab entries for shares without password protection.

You should still try implementing wins before moving on to other things because the fix is quite simple, and may make things work for you.

If I recall correctly, the Linkstation actually runs a version of Linux, so there are hacking posts out there which could enable things like NFS, SCP, or FTP. [http://www.nas-central.org/index.php/Main_Page](http://www.nas-central.org/index.php/Main_Page)

---

