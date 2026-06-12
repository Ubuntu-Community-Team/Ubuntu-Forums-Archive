---
title: "Samba Password and GUI vs. smb.conf file"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by xtraspecialj on 2010-09-18
I apologize for the length of this, but I want to be thorough.
This is a two part issue.
I have used Samba for quite some time and even though I am not completely competent on how all of it works, I get the basics.  I recently reformatted my computer and upgraded to 10.04.  I made a directory called /back in which I have all the Music, Movies, and Pictures that I wish to share with my Windows machines and my streaming media box (I use Mediatomb for that aspect).  Rather than going through the headache of manually editing Samba, I simply right clicked on /back in Nautilus, set sharing up, and was good to go.  Then I ran into the problem of Windows wanting a user name and password every time I tried to access it.  Since the data in the /back folder is not sensitive, I went into smb.conf ===Share Definitions=== section and changed the directory and file create masks to 0777 and in the ===Authentication=== section I set the security = share and guest account = nobody.  That solved the password issue. 

 Now I want to setup a folder that _**IS**_ sensitive and I want a user name and password prompt every time it is accessed.  I also don't want anyone to be able to see what is in the directory until they login (but I still want the main directory browse-able).  I went ahead and created the directory.  (Let's call it /private) and then I right clicked on it, changed the owner to my user name instead of Nobody, and put Others to No Access through the sharing options.  The /private folder now shows up in my Windows computer, but it only prompted me for user  name and password once.  Now it is not asking me for user name or password anymore when I access it each time.  It basically now has the same security as my /back folder it seems.  
  My problem is this:
--Neither the /back directory nor the /private directory are even listed anywhere in the smb.conf file.  How does Ubuntu even know to share these directories through Samba if it isn't even showing up in the smb.conf file (they are only showing up as shares in Nautilus and on my Windows computers)?  I am confident that if there were entries for each of these directories in the smb.conf file under the ===Share Definitions=== sections that I could go in and edit the settings in them and manually get it working the way I want.  I thought of going in and creating these entries manually, but I fear I will screw something up since I obviously am not understanding how these are even being shared in the first place.
Once again, sorry for the length and thanks in advance for any advice you may have.

---

### Post by HermanAB on 2010-09-18
Hmm, the problem with Samba is that there are vast numbers of configuration options and many of those options interact with each other in unpredictable ways.

Make a backup of your smb.conf, so that you can go back to the version that is mostly working.  Then experiment by changing ONE thing at a time and restarting smbd after each change to test it.  It is necessarily a slow and frustrating process.

The better solution is to install Windows Services for UNIX on the the Windows machines and installing NFS server on Linux.  NFS is much, much, much easier to configure than Samba.

---

### Post by xtraspecialj on 2010-09-18
Thanks for the quick answer and making me aware of Unix services for Windows (never thought to approach it from that angle).  
I am however, quite stubborn and want to figure out a problem before I abandon it for something else.  
The changing one thing at a time solution seems like a good idea, but also time-consuming for a full-time Dad, employee, and student.  

If there is anyone out there who still has maybe an answer or partial answer as to why Ubuntu can be sharing specific directories with my Windows machines while those directories aren't even listed in smb.conf, then I am still all ears.  Also, if anyone can tell me how to password protect certain directories while allowing full access to others, I'm still all ears.  

Thanks again,
Jordan

---

### Post by Paddy Landau on 2010-09-18
> **xtraspecialj said:**
> I am however, quite stubborn and want to figure out a problem before I abandon it for something else.
The changing one thing at a time solution seems like a good idea, but also time-consuming for a full-time Dad, employee, and student.
Well, between a rock and a hard place.

If you want to go Samba, have you installed the GUI configuration? [system-config-samba]("apt:system-config-samba") If you install it, I'd suggest you back up your existing smb.conf (as already suggested), restore it to its default, and try again with the GUI.

No guarantee that it will work, but it's another step to try.

---

