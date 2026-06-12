---
title: "Home File Server"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by Phette on 2008-03-18
I decided today that I want to mess around with networking around my home.  I have a desktop that I rarely use and I want to make it into a file server since I am usually on my laptop.  This is mainly just to learn a little about networking and to learn more about using a linux system.

I am running Ubuntu 7.10 on my desktop now, and it is using a wired connection to the internet through a wireless router.  My laptop is running Vista and connects to the internet wirelessly through this router.  Now, I mainly just want to use my desktop as a place to store media, although I will probably start to play with setting up an ftp server, web server, etc.. But for now, what would be the most reasonable way to share files on my local network?  I understand that it won't be that fast since I am only using a home computer, but again, I am just trying to learn.  I have read that Samba is a good program to share files on Linux-Windows networks, although a little more difficult to set up than other methods.

Thanks in advance for any help.

---

### Post by superprash2003 on 2008-03-18
yes.. you can use samba.. its pretty easy to setup.. just follow the instructions here [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Phette on 2008-03-18
Thanks for the response.

It does seem fairly easy to set up.  Now the only problem i'm really seeing is how to make the network visible to my Vista laptop.  I don't see it in network connections, nor can I connect to it with \\servername

---

### Post by Eiríkr on 2008-03-19
One of the keys is to make sure your Windows and Linux machines are both claiming to be members of the same workgroup.  If the workgroup names are different, you usually won't be able to see the one machine from the other.  

To make sure you're not dealing with a basic networking issue, make sure you can ping from one machine to the other.  On Windows, this looks like:
```
ping IP.ADD.RE.SS
```
... with the caps replaced with the numbers of your Ubuntu desktop's IP address.  Meanwhile, from Ubuntu, type:
```
ping -c 4 IP.ADD.RE.SS
```
The [font=courier]-c 4[/font] part tells ping to continue for a **c**ount of 4; otherwise, ping on Linux systems just runs forever, or until you hit Ctrl+C.  

If this works, make sure the workgroup names are the same.  If they are, open Explorer and check (this is in XP, not familiar with Vista) My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUP -> SERVER -> SHARE (with the caps replaced with the appropriate names).  If you still see nothing there and connecting to [font=courier]\\SERVER[/font] doesn't work, please post us the contents of your /etc/samba/smb.conf file.  You can display the file by typing either:
```
cat /etc/samba/smb.conf
less /etc/samba/smb.conf
```
[font=courier]cat[/font] just dumps file contents to the terminal screen, while [font=courier]less[/font] allows you to scroll around (useful for big files).  

Cheers,

Eiríkr

---

