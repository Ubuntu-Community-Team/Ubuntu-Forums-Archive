---
title: "NXclient Shadow session see's root instead of user."
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by Lisanels on 2008-06-30
I'm using no-ip and the nxclient applications to access my systems remotely, and they work great.  

The only issue I've got is that after upgrading from fedora 8 to fedora 9, the nxclient see's the user as 'root' instead of the real user (root session as opposed to 'Chris' session) that is logged in on the system.  

In fedora 8, this works perfectly and the user shows as 'lisa' where on 9 it shows as 'root'.  So, you are not permitted to connect to the root session.

I've been working on this for a while, and believe it has to do with the updates to gnome/gdm in fedora 9 and also might be in ubuntu 8.04.  That's why I'm posting on here.  

What I don't understand yet, is how the nxclient identifies the session, and determines what the username is.  I'm thinking the issue is with gdm or gnome.  

See the details below.  Two sessions show up, the one is my remote as a new session on the system, and the second is the local display that is really logged in as 'chris' not 'root'.

Lisa
                   
NX> 105 Listsession --type="shadow" 
NX> 127 Session list possible to attach:: 

 Display Type                Session ID               Services depth  Screensize  Status   Session Name Username
------- ------------ -------------------------------- -------- ----  -------------- ----------- --------------------- ----------------
1006    unix-gnome   0BA7AB4393AD503681FD41A0 -RD--PSA 24   1400x984       Running     Remote-Chris          lisa                            
0       X11-local    901BCB65BD434F0FF5133453 --D--PSA N/A  N/A            Running     Local display         root                            


NX> 105 Attachsession --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Remote-Chris-Shadow" --type="shadow" --client="linux" --keyboard="pc105\057us" --id="901B7C5BCB65BD4A6AC34F0FF5133453" --display="0" --geometry="available" 
NX> 596 ERROR: Cannot share session of user: root.
NX> 596 ERROR: User: root is not a NX user.
NX> 105 NX> 280 Exiting on signal: 15

---

### Post by Dorado on 2009-01-03
Hi Lisa,

I am seeing a similar problem using Fedora, see following thread:

```
http://forums.fedoraforum.org/showthread.php?t=209586
```

Did you ever come up with a solution?

Thanks,

Dorado

---

### Post by MarkJB on 2010-01-06
Just came across this problem myself.

EnableFullDesktopSharing = "1"
EnableAdministratorDesktopSharing = "1"

settings in the /usr/NX/etc/server.cfg (starts around line 609), allowed me to shadow a normal local session in karmic.

---

### Post by karagiozakos on 2010-01-07
> **MarkJB said:**
> 
EnableFullDesktopSharing = "1"
EnableAdministratorDesktopSharing = "1"


these 2 settings resolved the original error message for me too under 9.10 but I now get a different error:

  NX> 596 ERROR: Could not generate cookie: .
  NX> 596 Error: Unrecognized answer from nxnode: 0
  NX> 999 Bye.
  NX> 105 NX> 280 Exiting on signal: 15

---

