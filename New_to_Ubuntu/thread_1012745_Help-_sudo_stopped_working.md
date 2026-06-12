---
title: "Help- sudo stopped working"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by pollywog on 2008-12-16
I've been fooling around trying to get my new ATI card working by following this tutorial:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
-so far without success- and now I cannot sudo anymore. When I use the sudo command, I get this message (example):
```
matt@ubuntu:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:7796): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7796): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:7796): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7796): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault
matt@ubuntu:~$ 

```
I can use sudo to open a text file with gedit, but when I try to save to new file save, it wont. Instead I get the above message in the terminal. I also cannot log in as root. If I try to do so I get a message telling me that my last session lasted less than 10 seconds, and that there is a problem. Any ideas?

---

### Post by billgoldberg on 2008-12-16
> **pollywog said:**
> I've been fooling around trying to get my new ATI card working by following this tutorial:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
-so far without success- and now I cannot sudo anymore. When I use the sudo command, I get this message (example):
```
matt@ubuntu:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:7796): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7796): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:7796): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7796): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault
matt@ubuntu:~$ 

```
I can use sudo to open a text file with gedit, but when I try to save to new file save, it wont. Instead I get the above message in the terminal. I also cannot log in as root. If I try to do so I get a message telling me that my last session lasted less than 10 seconds, and that there is a problem. Any ideas?

It's nautilus that is giving you problems, not sudo.

---

### Post by Michael.Godawski on 2008-12-16
and what about

```
gksudo nautilus
```?

---

### Post by pollywog on 2008-12-16
```
gksudo nautilus
```
yields the same error message.

---

### Post by unutbu on 2008-12-16
> **pollywog said:**
> 
... when I try to save to new file save, it wont...  

My guess is that a partition on your hard drive might be full. Please post the output of 
```

df -h
du -sh /var/cache/apt/archives

```

The first command will show how much space has been used on each partition. If you find / or /home are nearly full, this might explain the problem.

The second command shows how much space is consumed by /var/cache/apt/archives. If you've confirmed that space is the problem, then the second command might suggest a directory whose contents can be safely deleted to create more space.

Since you can not log in as root, a solution would be to boot from the LiveCD, mount the full partition, use
```

gksu nautilus
```
to find and delete files (like /var/cache/apt/archives/*) to create some space.

---

### Post by pollywog on 2008-12-16
Thanks for your advice. Here is what I found by entering those commands
```
matt@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             188G   17G  162G  10% /
varrun                506M  124K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-22-generic/volatile
/dev/sda1             184G   85G   94G  48% /media/Vault
tmpfs                 506M     0  506M   0% /dev/shm
matt@ubuntu:~$ du -sh /var/cache/apt/archives
189M	/var/cache/apt/archives
matt@ubuntu:~$ 

```
I don't think that I'm running out of hard drive space. I don't understand what "df -h" tells me exactly, but I do notice that /lib/modules/2.6.24-22-generic/volatile is related to what I was doing before nautilus stopped working correctly. I was following the aforementioned tutorial which directed me to enter
```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```
followed by :
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


```
It seems logical that something in that broke my system. I guess that that's the downside of following tutorials- you may not know what the commands that you are pasting in do precisely.

---

### Post by pollywog on 2008-12-17
Well, after several reboots the system seems OK now - go figure.

---

