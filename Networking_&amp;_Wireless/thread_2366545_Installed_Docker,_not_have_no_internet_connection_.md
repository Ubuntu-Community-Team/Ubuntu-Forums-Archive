---
title: "Installed Docker, not have no internet connection after reboot [SOLVED]"
date: 2017-07-19
forum: Networking &amp; Wireless
---

### Post by compsciguy.it on 2017-07-19
[COLOR=#1D2129][FONT=Helvetica]Has anybody used docker on Ubuntu and later found they cannot connect to the internet? I started using it for the first time a couple days ago and the next day found I couldn't connect via wifi or ethernet!
I have been spending time troubleshooting ever since and have discovered that the drivers are now missing. Apparently the kernel is supposed to take care of this in my current Linux version, so I don't think it's just a matter of downloading new ones.

ifconfig reveals no wifi or ethernet adapters.
[/FONT][/COLOR][http://i.imgur.com/Z9Bybkz.png](http://i.imgur.com/Z9Bybkz.png)[COLOR=#1D2129][FONT=Helvetica]

lspci shows that they are there.
[/FONT][/COLOR][http://i.imgur.com/v0Co9rp.png](http://i.imgur.com/v0Co9rp.png)
[COLOR=#1D2129][FONT=Helvetica]
lshw tells me that they don't have their drivers.
[/FONT][/COLOR][http://i.imgur.com/aa2kxnT.png](http://i.imgur.com/aa2kxnT.png)[COLOR=#1D2129][FONT=Helvetica]

I have tried downloading and installing several packages by transferring them by usb, but nothing seems to work for me.[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]I looked in the kernel log file but nothing stood out as to what may be causing the problem.

I'll post screenshots of the above commands I ran and give a link to the kernel log file I put up on uploadedit.com.  Hopefully someone here can help me out so I don't have to do a reinstall of my os.  The version of Ubuntu I'm on is 16.04.2 LTS.
[http://m.uploadedit.com/ba3s/1500424958877.txt](http://m.uploadedit.com/ba3s/1500424958877.txt)
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]
I appreciate any help or ideas people might have. [/FONT][/COLOR]

---

### Post by QIII on 2017-07-19
Hello!

Please copy and paste all commands and their results as text between code tags rather than posting images.  That makes manipulating text easier for those who would like to help you.  

Large images are also problematic for our users with slow internet connections or data limits.  When images are appropriate, please use the attachment funtionality (the paper clip above tbe text entry area) which will leave a thumbnail image in tbe body of your post.

---

### Post by compsciguy.it on 2017-07-19
Ah yep.  No worries.  Sorry about that.

---

### Post by compsciguy.it on 2017-07-19
[COLOR=#242729][FONT=Arial]After considerable digging around and being on the brink of resorting to a fresh install of the operating system, I discovered a post: [https://unix.stackexchange.com/questions/93471/no-ethernet-wireless-connection-after-dist-upgrade-network-unclaimed](https://unix.stackexchange.com/questions/93471/no-ethernet-wireless-connection-after-dist-upgrade-network-unclaimed) on stackexchange.com by @weronika who suggested that booting from another kernel might help.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Not being sure how to do this I did more digging and found a post: [http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry](http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry)  on askubuntu.com by a user called @DaimyoKirby who explained how to change the grub file.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I made a copy of /etc/default/grub calling it /etc/default/grub.bak with the command[/FONT][/COLOR]
```
sudo cp /etc/default/grub /etc/default/grub.bak
```
[COLOR=#242729][FONT=Arial]and made the change suggested by @DaimyoKirby to /etc/default/grub by changing[/FONT][/COLOR]
> [INDENT][FONT=inherit]GRUB_DEFAULT=0[/FONT]
[/INDENT]
[COLOR=#242729][FONT=Arial]to[/FONT][/COLOR]
> [INDENT][FONT=inherit]GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 4.4.0-81-generic"[/FONT]
[/INDENT]

[COLOR=#242729][FONT=Arial](I found my previous version of the kernel by looking in the /usr/src directory). After this I rebuilt grub with[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]```
sudo update-grub
```[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]On reboot I was back to my previous version of the kernel and once again had an internet connection. I'm not sure if it was necessary but considering there were pending updates I did a[/FONT][/COLOR]
```
sudo apt-get updatesudo apt-get upgrade
```[COLOR=#242729][FONT=Arial]and a[/FONT][/COLOR]
```
sudo apt-get -f install
```[COLOR=#242729][FONT=Arial]as was suggested.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After this, I thought I'd try going back to the newer kernel I was on originally, hoping everything would still work, and it did. I made a copy of the grub file again just to be safe calling it grub.prev.bak, swapped the other backup file with current grub file, and once again rebuilt grub.[/FONT][/COLOR]
```

sudo cp /etc/default/grub /etc/default/grub.prev.bak
sudo cp /etc/default/grub.bak /etc/default/grub
sudo update-grub

```[COLOR=#242729][FONT=Arial]On reboot I was back with the latest kernel version I was using and still had internet. **ifconfig **[/FONT][FONT=Arial]revealed the once missing network interfaces.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I once again did a[/FONT][/COLOR]
```
sudo apt-get updatesudo apt-get upgrade
```[COLOR=#242729][FONT=Arial]and after this I was golden. =D[/FONT][/COLOR]

---

