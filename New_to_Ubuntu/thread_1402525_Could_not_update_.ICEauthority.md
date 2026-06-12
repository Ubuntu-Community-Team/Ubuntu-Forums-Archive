---
title: "Could not update .ICEauthority"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by myotis on 2010-02-09
I have  exact same problem as on an older thread. 

It appeared on booting up this morning, but without any known changes to the system since it booted up fine yesterday.

>First error message :
>Quote:
>Could not update ICEauthority file /home/graham/.ICEauthority
>And then:
>Quote:
>(usr/lib/libgconf2-4/gconf-sanity-check-2 has quit with state 256)
>After this I get an error that Nautilus cannot create the >following folders : /home/graham/Desktop and /home/graham>/.nautilus
>At this point nothing else happens, the systems stops >displaying an empty wallpaper and doesn't load anything else.

Initially I only had the update error and if I clicked on OK I seemed to boot normally. 

However, I followed the advice on the earlier thread and typed at Root shell

chown graham:graham /home/graham/.ICEauthority
chmod 644 /home/graham/.ICEauthority
exit

This then created the additional errors libconf and nautilus and the boot into blank wall paper.

I am now stuck. Its 9.10 updated from 8.04 and home is on a separate partition.

Urgent help would be very much appreciated.

Can I add that when I shut down, although I am logging in as "graham" I get a message saying I am logged in as "Graham M Smith"

Thanks,

Graham

---

### Post by Mustard on 2010-02-09
I'm not sure of the cause of the issue, but I was thinking that you might be able to work around the problem temporarily by creating a new user and logging in as that user, through GDM.  From there you at least have a working desktop to troubleshoot from.

---

### Post by myotis on 2010-02-09
> **Mustard said:**
> .. I was thinking that you might be able to work around the problem temporarily by creating a new user and logging in as that user, through GDM.  From there you at least have a working desktop to troubleshoot from.

Thanks, not sure what GDM is and not sure if I know enough to trouble shoot, even if I could get into the desktop.

I suspect I might end up just re-installing.

Graham

---

### Post by Wataru8675 on 2010-02-09
I had this issue awhile ago, I think.  Let's see if I remember how I fixed it...  Try typing in "nautilus" into your terminal.  Nautilus is the program that shows your desktop and navigation windows through your system (similar to Windows Explorer).  I'm not sure if that will permanently solve your issues......but I think that's how I started off.  See if that helps at all?  Sorry I'm not experienced enough to help you outright...

---

### Post by gdonwallace on 2010-02-09
I had the same problem, but was able to track it back to KlamAV (Antivirus software).  I had it running for about a day or so, I wanted to see if there were any problems with my system, OpenOffice was crashing for no reason, and I was not getting any help from the OpenOffice forums.  

Anywho, long story short.  When I ran KlamAV, it changed the permissions on my .ICEAuthority directory, this causing that error.  I changed the permissions back to what they should have been, and I have not had any problems.  Now, not saying that KlamAV is what is causing your issue, but it sounds like a program you are running has changed the permissions on the .ICEAuthority directory.

To find out, launch a terminal.  .ICEAuthority is in your home directory.  Type ls -al (this will list every file with permissions showning on the file)  You may have to scroll backwards to find the file, The owner of the file should show your login,  If it does not, issue the following command to change the owner **sudo chown login_name:login_name .ICEAuthority** and press enter.  Also the actual permissions on this file should be rw------- (first column in the display)

---

### Post by myotis on 2010-02-09
> **gdonwallace said:**
> 

To find out, launch a terminal.  .ICEAuthority is in your home directory.  Type ls -al (this will list every file with permissions showning on the file)  You may have to scroll backwards to find the file, The owner of the file should show your login,  If it does not, issue the following command to change the owner **sudo chown login_name:login_name .ICEAuthority** and press enter.  Also the actual permissions on this file should be rw------- (first column in the display)

Thanks,

Permissions are -rw-r--r--

Not sure how to change this, but I will try the chown command. 

Ok this made no difference.  So I assume I need to explicitly change the permissions

Graham

---

### Post by myotis on 2010-02-09
Thanks for everyones help, but I have decided to just re-install.

I need this computer working "now" and this is going to be quicker than fiddling about trying to fix this specific error.

I'm afraid that my experience has been that unless the first fix works, I always end up re-installing anyway, so I am trying to shortcut this.

Thanks again,

Graham

---

### Post by philinux on 2010-02-09
> **myotis said:**
> Thanks for everyones help, but I have decided to just re-install.

I need this computer working "now" and this is going to be quicker than fiddling about trying to fix this specific error.

I'm afraid that my experience has been that unless the first fix works, I always end up re-installing anyway, so I am trying to shortcut this.

Thanks again,

Graham

No need to reinstall. Right click on the file from nautilus and make the permissions match mine.

---

### Post by myotis on 2010-02-09
> **philinux said:**
> No need to reinstall. Right click on the file from nautilus and make the permissions match mine.

Thanks, but 

a) its too late, re-install underway, and 

b) how do I right click in Nautilus when Ubuntu won't launch


I could have done the latter before I ran the chown command, because I was actually getting into Ubuntu, but as I said in the OP after running this fix from the other thread, it stopped Ubuntu launching.

Graham

---

### Post by richardandrews on 2011-02-01
Thank you, you have helped me too :)

---

### Post by kakotako on 2013-02-06
> **gdonwallace said:**
> I had the same problem, but was able to track it back to KlamAV (Antivirus software).  

I am pretty sure ClamAV was responsible for it on my system. I had this problem the first reboot after running ```
clamav -r /
``` from the command line.

The strange thing is that I didn't run it as root but it gave .ICEauthority ownership to root. I didn't know normal users can change ownership to root. 

After reverting the ownership to me and setting rw permissions, the system boots fine.

---

### Post by sandyd on 2013-02-06
**Necromancing - Thread closed**

As per the Ubuntu Forums code of conduct, please do not post in threads more than one year old

Thanks!

---

