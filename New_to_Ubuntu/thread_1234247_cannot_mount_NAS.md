---
title: "cannot mount NAS"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2009-08-07
Hi
I have Jaunty installed and I have a NAS (synology 108j) on  my network
I have cannot seem to mount this NAS on my network from my Ubuntu computer.

I followed instructions in this blog: [http://www.marcus-furius.com/?p=59](http://www.marcus-furius.com/?p=59)

This is what I am entering into the terminal attempting to mount this NAS:

```
alex@alex-laptop:~$ sudo mount -t cifs //192.168.1.41/public /media/public -o nounix,uid=alex,gid=users,file_mode=0777,dir_mode=0777
```

Then I get prompted for a password

```
Password: 
```

I enter the password for the appropriate user account on the NAS and get this response:

```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

I thought I may be feeding it the wrong password and also tried the ubuntu login password, and also the NAS admin password. The result is the same.
I have read around various forums and blogs and think that I am making the connection to the server but there is something amiss with the credentials.
I tried to create a new user in on the NAS to experiment and did not get any further.

Can anyone see what I am doing wrong?

---

### Post by nandemonai on 2009-08-08
Have you tried the options:

```
,username=[shareusername],password=[sharepassword]
```

---

### Post by steinzeitmensch on 2009-08-08
Wow that did it.
So for all the others that come accross this post in the same situation as me, the line I put into the terminal was:
```
sudo mount -t cifs //192.168.1.41/public /media/public -o nounix,username=alex,password=xxxxxxxxxxxxx,file_mode=0777,dir_mode=0777
```
then I had to give the password for my user on in Linux, then I had to execute the mount with:
```
sudo mount -a
```

I took the next step which worked as well thanks to your valuable assisance which was to edit the fstab file with this line:
```
//192.168.1.41/public /media/public/ cifs nounix,username=alex,password=xxxxxxxxxxx,file_mode=0777,dir_mode=0777 0 0
```
This now mounts this NAS on startup.

Thanks very much!!!

---

### Post by Gabevee3 on 2009-11-02
Hello. I am new here, but not totally new to the unix/linux world. Just not as well versed as most of you. Rather than post a new query, I thought I'd drop in on this one since I have a similar problem.
 
I have set up an Ubuntu workstation that I have mounted a NAS device to (thanks to all here who replied to this on how to do so). However, I cannot see it as a user. I see it as root, and see all the folders in it as root.
 
How can I get it to be seen as a user?
 
I shared it and chmod with 777, but still cannot see it as a user other than root.
 
Thanks!
Gabe

---

### Post by steinzeitmensch on 2009-11-20
Hi Gabevee3,
Novices - You and me both!
As my post outlined, I finally got this line of code right and it works. How it works though, I would not mislead anyone into thinking I knew.

My advice is that you give it a reasonable attempt at searching around the forum and trying things out in the Terminal and the fstab file. If you still do not get where you want to be, start a new thread.
The guru's on here are very helpful and a great bunch of people. I am sure your problem will be solved before long
Good luck

---

