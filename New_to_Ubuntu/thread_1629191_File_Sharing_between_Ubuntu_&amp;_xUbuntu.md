---
title: "File Sharing between Ubuntu &amp; xUbuntu"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by immac.omnia on 2010-11-23
Salvete!

I am very new to (x)Ubuntu, and to Linux in general. I have a minimal knowledge of networking, as I've never required its use before. I'd like to know the most simple and easy way to set up a network with file sharing between two ubuntu and two xubuntu computers.


Many thanks.

---

### Post by lukeiamyourfather on 2010-11-23
Try NFS. Setting up the server and the client are both very easy.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Let us know if you have any questions or run into any issues.

---

### Post by lukeiamyourfather on 2010-11-23
Here is another NFS guide that is more straightforward. 

[https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html)

---

### Post by immac.omnia on 2010-11-23
Thank you very much! I'll try this as soon as I can - looks simple enough.   :)

---

### Post by Joe of loath on 2010-11-23
Samba is even easier to set up, but is usually much slower.

---

### Post by lukeiamyourfather on 2010-11-23
> **Joe of loath said:**
> Samba is even easier to set up, but is usually much slower.

I would not recommend Samba if all of the clients are Linux. To setup Samba ***properly*** it is vastly more complicated than NFS.

---

### Post by Joe of loath on 2010-11-23
I was thinking from the perspective that you can right click a folder and click 'share', but you're correct, it's not ideal.

---

### Post by Wtower on 2010-11-23
Hmm, I was wondering, why should one prefer NFS over SFTP really? I have set up my office network file sharing with SFTP, what is your opinion, should I change it to NFS?

---

### Post by max00355 on 2010-11-23
I know in Ubuntu you can just go to network and browse all the computers on ur network and you can even access them and take files from the other computer or put files on


heres an article on the subject: [http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/](http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/)

---

### Post by Sef on 2010-11-23
> Samba is even easier to set up, but is usually much slower.

Samba was designed for sharing between Linux and Windows machines. NFS was designed for sharing between Linux machines.

---

### Post by lukeiamyourfather on 2010-11-23
> **Wtower said:**
> Hmm, I was wondering, why should one prefer NFS over SFTP really? I have set up my office network file sharing with SFTP, what is your opinion, should I change it to NFS?

I would guess that NFS would be faster than SFTP, though I've not done any testing. NFS is also easier to setup by far. If SFTP works for you and/or you need the extra security then continue to use it. Though if starting from a clean slate I'd say NFS is probably a better option for a small office network of Linux machines.

---

### Post by immac.omnia on 2010-11-24
Thank you very much for all of the help concerning this. Before posting this thread, I had already discovered that Samba was not suitable to my interests. The NFS seems very like unto what I would need. I used the tutorials provided by lukeiamyourfather, which, while providing a much needed overview of the workings of NFS, nonetheless left a few details out for an ignoramous like me, perhaps. So, I went to Youtube.com and searched ''set up nfs ubuntu'' and this came up: [http://www.youtube.com/watch?v=NR9Ts8GV5Bo](http://www.youtube.com/watch?v=NR9Ts8GV5Bo)

The is the computer I want to be my server: Ubuntu 10.10 w/o internet connection (that is, I will have Internet during the setup process or after that when needed but normally not so) IP address 192.168.2.1   -   does that mean in order to make it a server I have to change it's IP address? or...

Please advise.


Also, does this video or any of the others posted on Youtube.com contain specific enough instructions for what I am trying to accomplish, i.e., simple LAN NFS file sharing between two (or more) Ubuntu and two (or more) xubuntu computers?

-immac.omnia :)

---

### Post by immac.omnia on 2010-11-24
Never mind the other question - I figured out (after a while) how to mount the NFS share using the second link provided by lukeiamyourfather, but my client computer with xubuntu can't find it.

My server's (Ubuntu 10.10)   IP is:192.168.2.1
My client's (xUbuntu 10.10)  IP is:192.168.2.2
and so on and so forth.

Basically, I type into my terminal on my server

     ```
gksudo nautilus
```     

then my password, and then I go to /etc and open Exports. If I type in what the guide tells me to type in, i.e.,

  /ubuntu  192.168.2.1/255.255.255.0(ro,sync,no_root_squash)
  /home    192.168.2.1/255.255.255.0(rw,sync,no_root_squash)

and then type in my terminal 

    ```
sudo /etc/init.d/nfs-kernel-server start
```    

it says something like ''/ubuntu doesn't exist.'' So, I changed the export file to:

 /local/ubuntu  192.168.2.1/255.255.255.0(ro,sync,no_root_squash)
  /home    192.168.2.1/255.255.255.0(rw,sync,no_root_squash)

and it mounts. And so I think ''Voila! It's done!'' I tried to go on my client computer, which again is running xubuntu, and then after typing

    ```
sudo apt-get install nfs-common
```

and then typing

    ```
sudo mount 192.168.2.1:/ubuntu /local/ubuntu
```

it says

    ''Mount point /local/ubuntu doesn't exist.''

Please help me resolve this issue.:confused: I am not very knowledgeable in this area, so I could really use some assistance.

-immac.omnia

---

### Post by lukeiamyourfather on 2010-11-24
You must create the mount point first.

```
sudo mkdir /local
cd /local
sudo mkdir ubuntu
```

---

### Post by immac.omnia on 2010-11-25
> **lukeiamyourfather said:**
> You must create the mount point first.

```
sudo mkdir /local
cd /local
sudo mkdir ubuntu
```
Where do I create the mount point - on the Server or client?

---

### Post by theozzlives on 2010-11-25
I have SAMBA, but I have a Windows-7 machine. If you go with NFS, and add a Windows box, Windows has a protocol the accesses Unix/Linux networks.

---

### Post by lukeiamyourfather on 2010-11-26
> **immac.omnia said:**
> Where do I create the mount point - on the Server or client?

The mount point is on the client side.

---

### Post by madjr on 2010-11-26
if you want quick file sharing without fuss or complication, then try **giver or empathy** lan neighborhood

Giver:

[IMG]http://www.ghacks.net/wp-content/uploads/2010/09/giver.png[/IMG]

[http://www.ghacks.net/2010/09/15/easily-share-files-on-lan-with-fellow-ubuntu-users-with-giver/](http://www.ghacks.net/2010/09/15/easily-share-files-on-lan-with-fellow-ubuntu-users-with-giver/)

empathy:

[IMG]http://farm4.static.flickr.com/3511/4024760178_c5773400b6_d.jpg[/IMG]

choose that last option: nearby people


*note that both computers must have those programs installed*

if you want something more universal, then try the other guides here.

---

### Post by immac.omnia on 2010-11-27
I know there is a way to automatically mount NFS shares on clients, via editing fstab, but I would really like to know - is there a way of automatically starting the NFS Kernel Daemon (I believe it's called) server either during the boot process or upon login, instead of going to terminal and then starting it from there?

Many thanks.

-immac.omnia

---

### Post by lukeiamyourfather on 2010-11-28
> **immac.omnia said:**
> I know there is a way to automatically mount NFS shares on clients, via editing fstab, but I would really like to know - is there a way of automatically starting the NFS Kernel Daemon (I believe it's called) server either during the boot process or upon login, instead of going to terminal and then starting it from there?

Many thanks.

-immac.omnia

It should already be running.

```

sudo service nfs status

```

If it doesn't run by default then try this.

```

sudo update-rc.d nfs defaults

```

---

### Post by immac.omnia on 2010-12-31
Ave Maria!

Please pardon my latency.

I figured out with your help and some research how to do it. You may mark this as solved. I am attaching a zipped PDF with very basic intructions as to how to complete this task.

Once again many thanks for all of the help.

Sincerely,

immac.omnia :)

---

