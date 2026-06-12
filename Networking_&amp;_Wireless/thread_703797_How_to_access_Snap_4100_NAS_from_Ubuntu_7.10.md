---
title: "How to access Snap 4100 NAS from Ubuntu 7.10"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by a.buck on 2008-02-21
Complete linux noob.

Basic question is as stated in the title.  How do I go about setting up persistent connections from Ubuntu desktop to multiple Snap 4100 NAS devices on my home network?

I enabled NFS in the SnapOS.  I am under the impression that Samba is only necessary for windows networking and is not necessary to connect a linux based desktop with a unix based NAS device.  Is this correct?

I assume that Ubuntu can authenticate directly with the Snap server and that there does not need to be a domain set up on the network, or an LDAP auth server, etc...  Is this correct?

When selecting "Places"->"Connect to Server", what is the "Service Type" that I should select? 

Any help would be much appreciated.


(BTW - I attempted to use search before posting and could not find an answer to my question....I must not know the right terminology to use??)

---

### Post by a.buck on 2008-02-22
Found this:  [http://www.marcus-furius.com/?p=25](http://www.marcus-furius.com/?p=25)

I followed the instructions listed on that web page customized for my situation as noted below:

My Snap server has a static IP:  192.168.11.21. 
The folder I want to share is //192.168.11.21/Private
The Windows name for the Snap server is:  "Snap3"
The user name I created on the Snap server is called "ubuntu"

1. I have no idea what this does or why I need Samba, but did it anyway:        
     sudo aptitude install smbfs

2. Create a directory on the ubuntu desktop to mount the snap server to:
      sudo mkdir /media/SNAP3

3. Copied the fstab file before making changes:
      sudo cp /etc/fstab /etc/fstab_backup

4. Edit the fstab file
      sudo gedit /etc/fstab

      At the end of the fstab file, added the following line:
      -----------------------------------------------------------------------------------------------------------------------------------
      //192.168.11.21/Private /media/SNAP3/ smbfs uid=ubuntu,gid=user 0 0
      -----------------------------------------------------------------------------------------------------------------------------------

5. Reload fstab
      sudo mount -a

      I am prompted for a password, which I type.  I then see the following error message:

     6909: session setup failed:  ERRSRV - ERRbadpw (Bad password - name/password pair in Tree Connect or Session Setup are invalid.)  SMB connection failed

I even went back to the snap server and changed the password to something else to make sure I had it right.  Still the same error.  I tried a different user name.  Still same problem.  Out of curiosity, what does "gid=user" mean?

The error message clearly says that something is wrong with the userid/password.  But why?

Any ideas?

Am I at least getting warm?

---

### Post by a.buck on 2008-02-22
I should add that when I go to "Places"->"Network", I can access the NAS just fine. 

I have to double-click "Windows Network", then the windows workgroup and I see all my root folders.  I can browse the NAS, open files, etc..

It seems to me that the "gid=user" portion of the fstab entry is troublesome.  Maybe it's just because I have no idea what it means?  It's the only thing I can think of.

---

### Post by a.buck on 2008-02-22
Yeeeeeehaaaaaaawwwwwwwwwww it's finally working.

I guess I picked the wrong person to copy.  The whole uid and gid thing was the problem.  Changed it to "username" and "password" and everything works just fine.

The following is now the last line in my fstab file:

-----------------------------------------------------------------------------------------------------------------------------------
//192.168.11.21/Private /media/SNAP3/ smbfs userid=ubuntu,password=test 0 0
-----------------------------------------------------------------------------------------------------------------------------------

If only I has known when I started that the keyword to search for was fstab.  (Mount and NAS help too)

---

