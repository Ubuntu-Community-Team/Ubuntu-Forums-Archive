---
title: "Apparently an update error"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by infiniteblank on 2009-10-23
So, I'm really really new to using Ubuntu.  I'm probably not at the level of computer knowledge I should be, but I swear I'm willing to learn and I've been making it on my own for a couple months now until I ran into this problem.

When I open the update manager it says there are five updates to preform.  I can list them if that would be helpful but I don't know if it would and I'd hate to waste my time if it wasn't necessary.  Anyway, when I go to preform these updates I get the following error message.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

If I do run 'dpkg --configure -a' it says it requires super user privilege.  Just to show how uneducated on this I am it took me a while to figure that out, but once I did and get super user privileges and run the line I get this back

"dpkg: parse error, in file `/var/lib/dpkg/updates/0012' near line 1:
 newline in field name `padding' "

I don't know what to do from here.

Please, if you help me with this I ask that you try and explain it as you would to a small child or your grandma.  I don't even feel like I'm posting this in the right spot but I don't know, have mercy?

---

### Post by delphiexile on 2009-10-24
try this in terminal :
sudo dpkg --configure -a

any pb , post it here.

---

### Post by oboedad55 on 2009-10-24
You need to run those commands with "sudo" in front of them This will raise your privileges temporarily. You'll be asked for your password, which will be invisible as you type it but not to worry it's there. This should do it, if not post back. As you did, error messages are always helpful.

---

### Post by infiniteblank on 2009-10-24
Thanks for lending a hand guys.  I followed your instructions and it looks like I got the same error back.

dpkg: parse error, in file `/var/lib/dpkg/updates/0012' near line 1:
 newline in field name `padding'

---

### Post by nothingspecial on 2009-10-24
Please post the output of

 
```
ls /var/lib/dpkg/updates/
```

---

### Post by infiniteblank on 2009-10-24
Alright, this is what I get back.

0000  0002  0004  0006  0008  0010  0012  0014  tmp.i
0001  0003  0005  0007  0009  0011  0013  0015

---

### Post by nothingspecial on 2009-10-25
Well, I have nothing in mine, on any of my five linux boxes.

```
rob@rob-netbook:~/Downloads$ ls /var/lib/dpkg/updates/
rob@rob-netbook:~/Downloads$ 
```
```

rob@server:~$ ls /var/lib/dpkg/updates/
rob@server:~$ 
```

```
rob@rob-laptop:~$ ls /var/lib/dpkg/updates/
rob@rob-laptop:~$ 
```

```
rob@rob-acer:~$ ls /var/lib/dpkg/updates/
rob@rob-acer:~$ 
```

```
Last login: Sat Oct 17 11:37:55 2009 from rob-netbook.local
suzie@suzie-computu:~$ ls /var/lib/dpkg/updates/
suzie@suzie-computu:~$
``` 

I would suggest removing those files from there, probably safer to move them first just incase

```
mkdir update.bak
```

```
sudo mv /var/lib/dpkg/updates/* ~/update.bak/
```

```
sudo dpkg --configure -a && sudo apt-get update
```

If everything appears fine then you can remove whatever those files are although it might be an idea to look at them first.
To remove them
```
rm -r ~/update.bak
```
)

---

### Post by infiniteblank on 2009-10-26
Alright, I'm pretty sure I followed your instructions and it cleared up at least part of the problem, I hope.  Now it appears all the updates that have come since I had the original error occur have come up to install.  However, when I start to install them a new error message comes up.

E: /var/cache/apt/archives/linux-image-2.6.27-15-generic_2.6.27-15.43_i386.deb: files list file for package `kdelibs-bin' is missing final newline

---

### Post by infiniteblank on 2009-10-31
I know it's probably bad form to bump your own topic, but I'm still in trouble here.

---

### Post by NoaHall on 2009-10-31
Here, do this - "cat /etc/apt/sources.list"

There will be a line with a weird name or in a incorrect format. Remove it.

---

