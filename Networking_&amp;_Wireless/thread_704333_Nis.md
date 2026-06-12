---
title: "Nis"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by expatCM on 2008-02-22
I have a permissions problem in accessing a NFS share.  I get permission denied unless I am root and then the share may be accessed.  So I am wondering why.

Could NIS not be working correctly?

From the client if I enter ypcat passwd I get a list of user names and id's from the server so that seems to be correct.

But if I enter id username on the client I get the local username and id and I was sort of expecting to get the username but the server id so that the name and id was common.

Am I correct in my  thinking?  If that is the case any idea where the problem could be?

---

### Post by rome-NY on 2008-02-22
what happens when you try to login as a user from the nis server. If you can't login then your nis is not working.

---

### Post by expatCM on 2008-02-23
I can putty to the server and log in as a user no problem.

I think I have done something quite bad on the client though.  I powered on this morning and it would not start up the desktop.  I used the live CD to stop the nis service from loading and tried again ....  this time all came up as normal.

So I have done something quite bad  in my set up on the client.  Now for the headache of working out what ......

---

### Post by Eiríkr on 2008-02-23
> **expatCM said:**
> I have a permissions problem in accessing a NFS share.  I get permission denied unless I am root and then the share may be accessed.  So I am wondering why.

Could NIS not be working correctly?

From the client if I enter ypcat passwd I get a list of user names and id's from the server so that seems to be correct.

But if I enter id username on the client I get the local username and id and I was sort of expecting to get the username but the server id so that the name and id was common.

Am I correct in my  thinking?  If that is the case any idea where the problem could be?

It's possible to set up NFS with UID/GID mapping without delving into the considerable complexity of configuring a NIS server.  After a good bit of online research and mucking about with config settings, I hit upon the solution described [post=4387032]in this post[/post].  Hope it helps!  :)

Cheers,

Eiríkr

---

### Post by expatCM on 2008-02-23
Thanks for sharing that link, it had some good points and well worth reading.

In my case I need to crack NIS since I have a total of four users on the home network and I want to keep life as simple as possible at the end of the day.

There are huge amounts of information on NIS to be found but it gets really confusing since much of what is said does not apply directly to Ubuntu and even when it does, it is assumed that all will work.  When it does not, finding out, or knowing HOW to find out, what are the problems is a real pain....

---

### Post by Eiríkr on 2008-02-24
> **expatCM said:**
> In my case I need to crack NIS since I have a total of four users on the home network and I want to keep life as simple as possible at the end of the day.

I'm curious -- with only four users, NIS seems like overkill...?  What does NIS offer you that's compelling?  I'm always curious to learn what other tools people find useful.  :)

Anyway, one thought that might help in configuring NIS is to try doing so via Webmin.  Sometimes I've found the Webmin GUI to be useful in helping me figure out precisely what options are available without having to first read through a couple of online tomes.  Webmin isn't part of the main Ubuntu repositories last I checked, but they do have .deb packages available, as well as their own apt repository, which may be found via [their website here](http://www.webmin.com/).  

I'm up to my eyeballs in work at the moment, but if I can squeeze some time out later, I'll see about setting up NIS on my own network here.  

Cheers,

Eiríkr

---

### Post by expatCM on 2008-02-24
Why .... well .... 

I started off with NFS.  But I had a problem in that the shares would work but only when mounted as root, access as a normal user always generated an access denied / permissions error.

So asking on the forums  I was told I need to reconcile the user names / groups between the client and server so that both are the same.  In turn it was suggested that nis was the tool to use unless I needed to share also with Windows in which case LDAP may be a better option.

Yes, I have Webmin installed on the server but what I find is that it is very tempting to click and away you go without really understanding what is going on.  I have also found that Webmin does not cover all programs so you still have to get your feet wet.  Sometimes I find it easier to edit a file than use Webmin  (but I can see that it will be a very popular tool for setting up home networks as it expands in the future).

Thanks for your interest Eiríkr

---

### Post by Eiríkr on 2008-02-24
> **expatCM said:**
> Why .... well .... 

I started off with NFS.  But I had a problem in that the shares would work but only when mounted as root, access as a normal user always generated an access denied / permissions error.

So asking on the forums  I was told I need to reconcile the user names / groups between the client and server so that both are the same.  In turn it was suggested that nis was the tool to use unless I needed to share also with Windows in which case LDAP may be a better option.

Interesting that someone recommended LDAP; Samba has its own built-in user mapping functionality, so you don't really need LDAP for Lin->Win sharing unless you're going whole hog and setting up a Windows-style domain with remote profiles and all that.  If you're running a company, that's probably the way to go; if you're an inveterate geek and you want to try setting it up, great; but if you're running a home network and you just want it to work simply, IMHO, that's more complexity than is needed.  ;)

NIS, on the other hand, looks simpler than LDAP (at least inasmuch as I've delved into the two).  More on NIS-based NFS sharing below...

> **expatCM said:**
> Yes, I have Webmin installed on the server but what I find is that it is very tempting to click and away you go without really understanding what is going on.  I have also found that Webmin does not cover all programs so you still have to get your feet wet.  Sometimes I find it easier to edit a file than use Webmin  (but I can see that it will be a very popular tool for setting up home networks as it expands in the future).

Yep, all valid criticisms of Webmin.  It can be a useful tool right off the bat, at least for seeing what some of the options are, but as you note, if you want a better understanding of how it all works, you're much better off diving in.  :)  

----------------------------------------

Back to NFS sharing, the setup I described at that linked post is indeed somewhat inelegant given the need to essentially hard-code values in the mapping files.  As far as I've had time to dig so far, that still looks like the best option if you've got Mac OSX clients for your NFS shares.  I may change my tune once I've had time to figure out how to configure a NIS server on the Mac :) -- The NFS-NIS combo is certainly much prettier now that I think it through, given the dynamic name resolution.  

Coming back to your situation, I looked again at [font=courier]man exports[/font], and found the following (bold italics mine):
> Static  mapping  is enabled by using the **map_static** option, which takes a file name as an argument that describes the mapping.  NIS-based mapping [NB: enabled using the **map_nis** option] queries the ***client's*** NIS  server to  obtain a mapping from user and group names on the server host to user and group names on the client.

So it sounds like your local (client-side) user should *never* receive the server-side UID/GID when typing in [font=courier]id[/font] on the client machine.  Moreover, it sounds like instead of *one* NIS server on the NFS *server  machine*, you need to have NIS servers running on *all* of your NFS *client machines*.  If you can get that set up (and it sounds like you've already done it once for your NFS server machine), NFS sharing should presumably work just fine.

Another important note from [font=courier]man exports[/font]:
> **map_nis**
This option enables NIS-based uid/gid  mapping.  For  instance,  when  the  server encounters  the  uid  123  on the server, it will obtain the login name associated with it, and contact the NFS client's NIS server to obtain the uid the client associates with the name.

In  order  to  do this, the NFS server must know the client's NIS domain.  This isspecified as an argument to the **map_nis** options, e.g.

**map_nis=foo.com**

Note that it may not be sufficient to simply specify the NIS domain here; you  may have  to  take  additional  actions  before  **nfsd**  is actually able to contact the server. If your distribution uses the NYS library, you can specify one or more NIS servers for the client's domain in **/etc/yp.conf**.  If you are using a different NIS library, you may have to obtain a special **ypbind** daemon that can be  configured via **yp.conf**.

Hope this helps!

Cheers,

Eiríkr

---

### Post by expatCM on 2008-02-25
Hi Eiríkr,

thanks for following through.  I think I have a lot more to explore now .... if I did this for a living I think I would probably quit but now I have some challenges to explore....  off on my own....  :)

There is one thing I do not understand.  I want to find out if the server is running correctly and so I use rpcinfo to look at the registered RPC programs. Nice list but what I do NOT see is ypbind and that to me is a concern.

Do you happen to know if this is a valid concern?  The way I interpret this is that something fundamental is missing to bind the clients to the server.

<QUOTE>
rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  57628  status
    100004    2   udp    655  ypserv
    100004    1   udp    655  ypserv
    100004    2   tcp    656  ypserv
    100004    1   tcp    656  ypserv
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32772  nlockmgr
    100021    3   udp  32772  nlockmgr
    100021    4   udp  32772  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  59350  nlockmgr
    100021    3   tcp  59350  nlockmgr
    100021    4   tcp  59350  nlockmgr
    100005    1   udp  32773  mountd
    100005    1   tcp  39459  mountd
    100005    2   udp  32773  mountd
    100005    2   tcp  39459  mountd
    100005    3   udp  32773  mountd
    100005    3   tcp  39459  mountd
</QUOTE>

---

### Post by Eiríkr on 2008-02-25
> **expatCM said:**
> There is one thing I do not understand.  I want to find out if the server is running correctly and so I use rpcinfo to look at the registered RPC programs. Nice list but what I do NOT see is ypbind and that to me is a concern.

Do you happen to know if this is a valid concern?  The way I interpret this is that something fundamental is missing to bind the clients to the server.

I think it might very well be a concern, though I don't know for sure.  I'm curious why your rpcinfo results show "ypserv"; I can't seem to get ypserv to run just yet, only ypbind.  Anyway, from the ypserv man page:
> **DESCRIPTION**
The  Network Information Service (NIS) provides a simple network lookup service consisting of databases and processes.  The databases are  **gdbm** files in a directory tree rooted at **/var/yp**.

The  **ypserv**  daemon  is  typically activated at system startup.  **ypserv** runs only on NIS server machines with a complete NIS database. On other machines  using  the  NIS services, you have to run ypbind as client or under Linux you could use the libc with NYS support.  **ypbind**  must  run on  every machine which has NIS client processes; **ypserv** may or may not be running on the same node, but must be running somewhere on the  network. On startup or when receiving the signal SIGHUP, **ypserv** parses the file **/etc/ypserv.conf**.

So since you ran rpcinfo on the server, it sounds like the lack of any ypbind processes is not a problem.  Try running [font=courier]rpcinfo -p[/font] on a client machine (or add the client machine's name after the "-p" and run on the server) and see if that shows any running ypbind instances.  

Now to figure out for myself why I can't get ypserv to run... :)

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-02-25
Got ypserv working, and most annoyingly I really don't think I changed anything -- it just started working.  Anyway...

---

### Post by expatCM on 2008-02-27
I have not solved this yet but I am moving forward.

I got fed up and so did a apt-get –purge remove portmap nis nfs-kernel-server and then installed them again.

As soon as they were installed I started the nis service and then had a look at what was running with rpcinfo -p.  ypbind was there and so I felt quite happy.  ypserve was not but I think that does not load until the database is built.

I then moved on to set things up and build the database.  I ran /usr/lib/yp/ypinit -m

It ran ok but there was a problem which may be the cause of my headaches.  In running the program you are prompted to add nis server names ....  the program tells you what the identified entry is and then invites you to add more and then press cntrl-D to move on.   In my case the first entry (which cannot be changed) is the host name and not the nis server name.  So when the program completes the nis master server name is incorrectly listed as the host name.

I thought ok ...  so what ....  

Well if I then run rpcinfo -p again the list of services had changed and ypbind was no longer on the list and of course ypwhich cannot communicate with ypbind because it is not running.

So it sounds a little like the problem is outside of nis.  

Some clues here
[http://www.yolinux.com/TUTORIALS/NIS.html](http://www.yolinux.com/TUTORIALS/NIS.html)
but they do not quite relate to the Ubuntu file structure.  

I think I will uninstall everything again and try and work out what next .....

---

