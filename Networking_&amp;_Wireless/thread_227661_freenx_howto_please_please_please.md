---
title: "freenx howto please please please"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by brickbat on 2006-08-02
Freenx in Dapper has serious problems.  There is a howto but it has problems. The version installed via the additional repo according to the howto is old.  Therefore, when you use the latest Windows client from nomachine (I have searched the internet and been unable to find a download of the older version), there is an incompatibility.

So, ok, try downloading the debs from nomachine and installing them directly.  On their site, it says it runs with Ubuntu 6 - wrong.  There is a dependency that cannot be met.  Again, I have searched the internet for this file to meet the dependency - no luck.  I'm sorry, I can't give exact names of the files now because I'm not at the machine.

It shouldn't be this hard.  I admit I am no expert - but this is very very frustrating.  Can someone that actually knows what they are doing please please do a proper howto for installing the latest version from nomachine.

---

### Post by harisund on 2006-08-02
Ok ok ok relax relax relax :) 

The thing is, the server and the client need to be the same version. 

So what I would do is this. 

Search (using dpkg --list | grep nx) for all nx related packages that you might have installed (also include dpkg --list | grep NX) and *purge* them all. 

Then use the seveas repository to install freenx (sudo aptitude install freenx). Don't do anything else, accespt the default values. 

Finally download a Windows 1.5 NX client. I am not able to find it on Google anymore. Thank God I still have an old client with me. I have uploaded it [here](http://www.cct.lsu.edu/~hsunda3/nxclient/)

Then just use the Windows client. 

If your NX server is behind a router, remember to check the SSL encryption option. 

Finally, you need not worry about keys. You can use the regular user name and password you use in your Ubuntu machine on the NX client. 

Also, what machine are you having? If it is Xubuntu, you will need to make a change.

Also, I don't know how to get version 2 working with Ubuntu. And I don't care really since 1.5 works just super awesome fine.

---

### Post by brickbat on 2006-08-02
harisund, Thank you so much.  I have searched for this file in every search engine possible.  All I got was links to the nomachine downloads page.

I installed the 1.5 client and it worked perfectly.

---

### Post by harisund on 2006-08-02
Hmmm.. that worries me indeed....I downloaded it from  [Cnet](http://downloads.zdnet.co.uk/0,39025604,39153612s,00.htm) ... in fact the link is still there, but no search engine shows it.

I searched Google for the string ["CNET Windows NX 1.5 download"](http://www.google.com/search?q=cnet%20windows%20nx%20client%201.5)
and it came up. 

Maybe NoMachine requested Google to remove that link

Oh well. Glad you got it to work.

---

### Post by Predseda3D on 2006-08-02
> **harisund said:**
> Ok ok ok relax relax relax :) 

The thing is, the server and the client need to be the same version. 



Hi,

the server and client doesn't need to be the same version. Read next please.

I have Debian Etch and have installed this:
freenx             0.5.0-2
nxagent          1.4.92+1.5.0-11
libxcomp1       1.4.92+1.5.0-11
libxcompext1   1.4.92+1.5.0-11
nxlibs             1.4.92+1.5.0-11

from deb [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) sid nx

And everything work great for me. I tested this with NX Client 2.0.0-98 and NX Client 1.5.0-138.
I tested it with FreeNX 0.4.4+0.4.5-4 and work good too.

If i use NX Client 2.0.0 i must use some hack in nxnode to work for me.

If somebody have problem with NX Clients versions 2.0.0 and FreeNX 0.4.x or 0.5.0, you can read wiki about this problem and solution here: 
[http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving]("http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving")
or here:
[http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0]("http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0")

Hope that will help. 

Predseda

---

### Post by harisund on 2006-08-02
Wow! Thanks for that piece of information Predseda. 

Perhaps the seveas repository can be upgraded with the patch. 

Do you see any huge performance gains in 2.0 over 1.5? If not I guess Windows users could happily do a 'apt-get install freenx' and use the 1.5 client itself. 

But again, thanks for that. I will have to try it out myself :)

---

### Post by LBailey on 2006-08-03
You can also get NX Client 1.5 at
[http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768](http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768)

I have one question though. Does your resume session work properly? 
Mine resumes after "Suspending" the first time, but then I can't close the stupid window (to either "Suspend" or "Terminate")!
Grr

---

### Post by harisund on 2006-08-03
Hmmm...now that you mentioned it I gave it a try .. and yeah after I suspend, it resumes but then goes full screen and becomes sort of unmanageable.. and doesn't work ...

bad luck I guess.. I don't really mind though ..

---

