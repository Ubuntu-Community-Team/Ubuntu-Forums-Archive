---
title: "Would like assistance with home network set up ..."
date: 2010-11-09
forum: New to Ubuntu
---

### Post by CDSH on 2010-11-09
I am trying to set up a home network comprised of an Ubuntu 10.04 PC, Two Windows 7 PCs, and one Windows XP PC.  Could someone assist me with the packages and information required to make the network function ?  

I am a new user of Linux - (read Windows refugee wannabe).  So far, my efforts to get the different PCs to communicate have not been successful.

Thank you in advance !

---

### Post by J V on 2010-11-09
Windows doesn't play well with others, not even other windows' :)

If you set up a shared folder on a windows box you should be able to hook up to it from ubuntu (Go to places > Network)

---

### Post by Image0fman on 2010-11-09
Have you installed the SAMBA package?

---

### Post by CDSH on 2010-11-09
> **J V said:**
> **Windows doesn't play well with others, not even other windows' :)**


Yes, Windows is a egocentric anti social system - That is why I am  attempting the great escape.  I'm also getting tired of cloning my  Windows OS every three days just to avoid shelling out more $$$ for  another MS OS - but that's kind of a tangent off the subject ...

> **J V said:**
> **If you set up a shared folder on a windows box you should be able to hook up to it from ubuntu (Go to places > Network)**

I have downloaded and installed SAMBA , but I have no idea if all of the necessary items were included when I did.

Here is what I have done so far:

On Linux Box: 
 
>Places 
  >connect to server 
   >windows share 
      entered  IP address - xxx.xxx.x.xxx
       ( found on Windows machine IP address using Network and sharing center... 
          clicked on Local Area Connection 
            On Status screen click Details tab ) 
   Entered Windows7 User name - XXX 
    
   Ticked "Add Bookmark" box - Bookmark name = XXX. 
 
On Windows7 Box: 
 
Changed The monstrosity called "Homegroup"  to  Workgroup then transfered wanted files to Public Folders. 

Now, I can access the files in the Windows' Public Folders (at least for today).  However, Although I can see my Linux Box on Windows, I can NOT access anything there.  

Would you happen to have a suggestion as to how to make the process function automatically and work in both directions ?

---

### Post by Hippytaff on 2010-11-09
> **Image0fman said:**
> Have you installed the SAMBA package?
 
+1
 
Samba is the way forward :-)

---

### Post by pricetech on 2010-11-09
For a new user it's usually easier to use Synaptic Package Manager.  Search for system-config-samba and install it.  That will give you all the Samba you need and a handy configuration tool under System - Administration - Samba.

Share what you want on your Linux box and windows should be able to access it without a problem.

Matching the workgroup name just helps with browsing.  You can connect even if the workgroup names don't match.

---

### Post by bioterror on 2010-11-09
> **CDSH said:**
> 
Now, I can access the files in the Windows' Public Folders (at least for today).  However, Although I can see my Linux Box on Windows, I can NOT access anything there.  

Would you happen to have a suggestion as to how to make the process function automatically and work in both directions ?

Download [Putty Tray]("http://haanstra.eu/putty/") and connect to your linux box from windows with SSH. Now you can use your linux box remotely.

---

### Post by jadlerhalofan on 2010-11-09
Ask yourself if you really need the Windows OS on all of those computers. Linux is designed for networking and server applications. You might find that Windows is best suited as a dual booted OS for mission critical items.

---

