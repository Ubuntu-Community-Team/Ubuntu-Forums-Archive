---
title: "Can not set up NFS network"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by ranch hand on 2009-04-07
I have 2 boxes running Intrepid.  I have a linksys router.  I installed "nfs-kernel-server nfs-common portmap" on the box I want to use as server.

I then need to have a /etc/host and /etc/exports and some other files.  I do not have these files.

What the heck am I doing wrong?

I have several "guides" to setting this up and they all seem to agree that this is simple.
I think that I may be too simple.

---

### Post by joeashcraft on 2009-04-12
/etc/exports lists the files and folders that are available for remote mounting over NFS. It won't work without that file. 

I used _[this how]("http://ubuntuforums.org/showpost.php?p=1456895&postcount=1")_ to with success.

---

### Post by HermanAB on 2009-04-13
See this for the one liner required in the exports file:
[http://aeronetworks.ca/nfs-howto.html](http://aeronetworks.ca/nfs-howto.html)

Then restart the NFS server to make it read the exports file.

---

### Post by ranch hand on 2009-04-13
joeashcraft
Thanks for your post.

I will try that guide.  I didn't use that one because of the date.

Are you by any chance related to any ashcrafts in W.Va.?

HermanAB
Thanks to you too.

I really want to get this going.

I never found that guide at all and will give it a whack.  I may need some guidance on that one but I am not sure.

It is getting late here and I have to be up early tomorow.  I will try this stuff in the next 3 days sometime.

We are in the middle of moving.  I is hectic.

---

### Post by joeashcraft on 2009-04-13
As far as I know I'm not related to any W Virginians.

> **ranch hand said:**
> 
I didn't use that one because of the date.


One thing I've found about Linux is that a lot of things are backward compatible. What I mean is that if you use an old How To it will still probably work. If something has changed there will probably be a note in the .conf file or when you run the program it will tell you "this directive is outdated, use this new one".

Good luck!

---

### Post by ranch hand on 2009-04-13
Got the horse trailer unloaded and ready to get back to the ranch.  I won't be able to get it out loaded because of the rain that we will get tonight and tomorrow.  So just out, set trailer by shop to load, and get a load from the bunkhouse for the truck and back in the morning.  54 miles of mud - probably 2 hours.

I tried that guide.  I still do not have an export or host file.  I tried the other guide (for Mandriva) and either could not get those packages or they are part of ones I have.

I don't see any purpose of creating an export file, i don't have a host file and I don't know what else I don't have.

This sounds like a real simple thing to set up in everything I read.  But my outcome is less than optimal.  I mean, geez, I can't even have trouble with setup because I can't get the componants to set up.

I can share files by using ssh so I know that communication is very possible and it sets up easy, but it is not the functionality that I want.

I don't know what to do.  A trip to the ranch may help me think.

---

### Post by HermanAB on 2009-04-13
Well, the /etc/export file is the configuration file for the NFS server.  Without it, it won't work.  It won't work without the /etc/hosts file either.  You have to create these files, else you are just wasting your time.

---

### Post by ranch hand on 2009-04-13
Haven't left for the ranch, splitting headache.

I have been looking at:
```

man nfs

```
I need to have lines in fstab and mtab at least.  There are no lines there either.  I have no idea what else I am going to need.  I do have the man files but that is about all I can find having to do with nfs.  No guide talks about having to build or rebuild files and folders to any extent.  I have no idea where to start.

---

### Post by joeashcraft on 2009-04-13
What ever you put in /etc/fstab will be mounted at boot time. You don't need your NFS mounts in /etc/fstab unless you want them to be mounted automatically, or if you want users to be able to mount them manually (you can always mount manually with sudo). 
/etc/mtab shows the currently mounted filesystems (so does the mount command).

The /etc/exports file is absolutely necessary to the NFS server. If you don't have /etc/exports it will be created when you try to open it with an editor (i.e. sudo vim /etc/exports).

---

### Post by ranch hand on 2009-04-15
OK, I think I have the stuff I need now.  I uninstalled all nfs related items and reinstalled with apt-get.

Now I am having the problems that I expected.

What in flinderation am I supposed to do with this;
> 
Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

Is the name of the "server" the name that is in the terminal heading?  If so, what is all this "server.mydomain.com" bussiness?  Is this the format inwhich it needs to be entered in the file?

---

### Post by joeashcraft on 2009-04-16
> **ranch hand said:**
> 
Is the name of the "server" the name that is in the terminal heading?  If so, what is all this "server.mydomain.com" bussiness?  Is this the format inwhich it needs to be entered in the file?

"server.mydomain.com" is used as an example. Another example could be "nfs.google.com" if there was an NFS server at that location. It's recommended that you use an IP address rather than a domain name. So your mount command could look like
```

mount -t nfs 192.168.1.100:/files1 /files2

```
where 192.168.1.100 is the IP address of the NFS server, /files1 is a location on the server and /files2 is a location on the client. Make sense?

---

### Post by ranch hand on 2009-04-16
YES, that makes great sense.  I don't know what people have against numbers.

Maybe they learned to spell better than I did.

Thank you very much.  I will try it tomorrow when I am awake.

Don't have to move, another storm. not too bad this time.  Saterday may be a possibility.  I need to get moved there is a guy that has called twice now trying to hire me.  He is out 35 miles and I don't want to drive that far (probably 1 hour each way) but he does not have a bunk house.  When he called today he said he has a nieghbor that has a house and needs some help so that they could probably keep me busy at least all summer.

A lot of calves died in the storms (and lambs).  When the snow shrinks down as it melts it just pulls the fence wire with it and flattens the fence.  They need a lot of fence fixed.

Ah the romance of cowboying.

---

### Post by Elfy on 2009-04-16
Just a FYI - I fought this a while ago - I ended up at that same link - in the end [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) cracked it for me once I had got the fstab sorted.

I mount mine through fstab -

this is my /etc/exports

> /mnt/data 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)

/mnt/media 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)

/mnt/music 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)

and the corresponding fstab lines

> 192.168.0.2:/mnt/data /mnt/data nfs rsize=8192,wsize=8192,noexec,nosuid
192.168.0.2:/mnt/media /mnt/media nfs rsize=8192,wsize=8192,noexec,nosuid
192.168.0.2:/mnt/music /mnt/music nfs rsize=8192,wsize=8192,noexec,nosuid

---

### Post by ranch hand on 2009-04-17
I haven't died or anything.  I am just trying to get this to work.

Not much luck yet.

Just messages that the other box does not exist.  I am pretty sure that both do exist, they are both in a 3'x4' area but the messages make me wonder if I am halucinating.

Everything still works fine with openssh transfers.

---

### Post by ranch hand on 2009-04-17
forestpixie

I would like to know if you used the NIS stuff.  I have the Howto in my bookmarks and have used it some but with no luck.

Some threads have said that none of that is needed, just instal the nfs stuff and go.  this does not seem to work at all.

The reason that I need this is to transfer files and folders.  Openssh works.

The only reason I don't give up on this is that I am stubborn, I started to do this and want to make it work.

But, I do have a life and am starting to wonder if this is worth it.

Right now I am trying to get the hosts.allow file straight.  Better get back to it.

---

### Post by Elfy on 2009-04-17
I am pretty sure that I only used the NFS server and client stuff on the wiki - however there's a chance I did soemthing prior to that - I have checked my bash history but nothing jumps out and bites me.

If I'm honest this was the first time that I had done this and am not the best person to try to help :(

---

### Post by ranch hand on 2009-04-17
Well I am giving this up for now.  All I am getting is that niether computer exists.

I am only trying to hook the partition I am on now to the the other computer.  It is not going at all.

With openssh I can, in 2-3 minutes be hooked up from a new install, from any HDD, internal or external.  Iguess I better stick with that and forget it.

---

