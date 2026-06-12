---
title: "Here comes another Newbie!!"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by timothy48342 on 2011-04-22
I always seems to have problems adding software packages in Linux.
I gave up on other versions of linux for same reason, even retail ones.
I never had a problem with Windows, Mac, Dos, Applesoft. There is
something anti-intuitive for me when it comes to This.

So here is a little success so far:
I downloaded the Ubuntu 10.10 Live CD ISO
Burnt the ISO to a CD.
Eventually I got Ubuntu running properly direct from the CD.

By the way anyone having trouble getting that far...
My first CD got a lot of errors and wouldn't load the GUI.
Using Nero my first blank cd was unbranded and reported as 657MB
The ISO is larger than that so I enabled overburn. I burnt at maximum
speed. (24x burn speed, I think.)

My second CD worked fine. I used a different brand CD (memorex lightscribe)
that reported 703MB and dropped the burn speed. (Still with Nero)
I read somewhere that I should burn at the slowest speed, but 4x would have
taken many hours, so I did 16x.
So I think either brand, size, or speed could have been the problem.

Now my question:
"Still running Ubuntu directly from the CD, I downloaded Trucrypt
from trucrypt.org/downlloads selecting linux package:
"Standard - 32-bit (x86)" It is a .tar.gz
It extracted fine and the file "truecrypt-7.0a-linux-x86" is supposed to be
an executable file. (I couldn''t fine a .deb file for it).

So how do I execute it?
[B]I found the checkbox for "allow executing file as executable"
under properties, permissions, but when I check the box,
it automatically uncheckes itself about a second later.
The allow execute box won't stay checked.[/B]

The file is located on what WinXP calles the D: drive, which was formatted
by winXP during installation, but the file was downloaded by Ubuntu, 
and while using Ubuntu, I can create, edit and delete files is that
same location without messing with permissions.

Thanks in advance,
Timothy48342

BTW, I am posting this from within a running Ubuntu environment.
Yea!!):P
It successfully recognised everything it needed to get up and running
and on the Internet with no problem. (except for my burning techniques)
Much better than my last experience with Linux a few years back with a 
purchased retail version.

---

### Post by frup on 2011-04-22
That is not the easy way to install anything in Ubuntu.

With Ubuntu you use repositories, which are like an app store or market place in iTunes, iPhones, Android phones etc.

What you do is you open the application called software centre, you then search for what you want to install and then install it. The application will set everything up for you.

Until you know what you are doing do not even attempt to install application from websites, that is just not the way it is done and until you know why you might need to do it from a website instead, you don't need to.

If you want to learn more about the installation of software learn about the following things: Repositories, Software Centre, Synaptic Package Manager, Apt (apt-get), dpkg.

---

### Post by alphacrucis2 on 2011-04-23
Actually truecrypt is very easy to install via the .gz archive. You just download it and double click it to extract the truecrypt installer which you then run. It will ask you to accept the licence. Almost as simple as installing a deb package. AFAIK truecrypt is not in the standard Ubuntu repo's but there may be a ppa although I don't see what the point of a ppa would be in this particular case.

---

### Post by clhsharky on 2011-04-23
timothy48342


Welcome to Ubuntu Forums.

The best way I know to getting started is with-

Free Ubuntu Pocket guide by Keir Thomas
PDF
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

I'm not saying RTFM, but this guide is very helpful  with Ubuntu.



Sharky

---

### Post by timothy48342 on 2011-04-25
ok, I figured this out. Thanks for the help, people.

The reason I wasn't using a Software Center was because I searched and it wasn't there. I have since found Easy Crypt available through there. I imagine that might work, but getting the real truecrypt installed should not be that difficult.

I think the thing that was messing me up was where I had the download sitting. I started typing commands and found I couldn't change ANY permissions on files there. All files there are -rw------- and all folders are drwx------
It is a partition created and formatted by WinXP at the time of install and "mount" says:
/dev/sda7 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
I don't know what most of that means, but I bet that windows or foriegn filesystems have the permissions locked to default values when allowing it to be mounted automatically by just clicking it in the GUI. (that's the only may I know how to mount right now)

On a small test file called test...
"ls -l" says:
-rw------- 1 ubuntu ubuntu 372 2011-04-26 00:44 test
chmod does not get any error. "chmod -v u+x test" says:
mode of `test' changed to 0700 (rwx------)
But it doesn't really change.

So, I dragged executable to the desktop and changed it to allow and doubleclicked and installed and everything works fine. 
Truecrypt was able to open my existing crypts, so all is good.

This issue can be "closed" if you guys do that here. I just wanted to report back for the sake of any other new user that runs into the same problem.

By the way, Sharky, the pocket guide...
> **clhsharky said:**
> timothy48342
...
Free Ubuntu Pocket guide by Keir Thomas
PDF
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
...

...was quite useful as a starting point to figure things out.
Fell free to tell me to RT_M any time. (With a link to useful manual, of course)

Thanks again.
Timothy48342

---

### Post by jtarin on 2011-04-26
> **timothy48342 said:**
> 
Fell free to tell me to RT_M any time. (With a link to useful manual, of course)

Thanks again.
Timothy48342[RTFM]("http://www.manybooks.net/titles/boyscoutsofamerica2955829558.html")...the original :P

---

