---
title: "Sending / Receiving Files Wirelessly Between Ubuntu Computers?"
date: 2020-04-05
forum: Networking &amp; Wireless
---

### Post by Gregory.Opera on 2020-04-05
I have multiple computers in my house that run various versions of Linux Mint or Ubuntu, though soon they will *all* be running the upcoming Ubuntu 20.04 LTS ("Focal Fossa").

At the moment, if I want to move files between computers, I either put the relevant files onto a "thumb" / flash drive (for sensitive or large files) or I e-mail them to myself (for non-sensitive or small files)... Regardless of how I currently send / receive files though, it is a lot of mucking around.

What I would like to do - preferably using something with a *graphical front-end* (though I am not *entirely* opposed to a Terminal solution, if it's not too much mucking around) - is send / receive files between each computer wirelessly, over our wireless network...

Can anyone recommend a program which will allow me to do this?

---

### Post by ch33zw1z on 2020-04-05
The software you choose won't care if it's wireless or wired, imxp. There's the tried and true FTP, although if you plan on going outside your own network then SFTP would be better.

Are you looking to centralize the storage? or just individual files from time to time?

---

### Post by The Cog on 2020-04-05
I would recommend using sftp. Install openssh-server on the computers you want to connect to, then use your normal file manager as the client (probably nautilus, but as I'm on xubuntu I use its default file manager thunar). To connect to another machine switch to a typed location (as opposed to buttons) and enter something like "sftp://username@ipaddress". Then you can drag and drop between that remote machine and local file manager windows. Picture attached.[ATTACH=CONFIG]285405[/ATTACH]

You may also want to look at password-less logins: [https://www.linuxbabe.com/linux-server/setup-passwordless-ssh-login](https://www.linuxbabe.com/linux-server/setup-passwordless-ssh-login)

---

### Post by Autodave on 2020-04-05
*Teamviewer* is another option.

---

### Post by ajgreeny on 2020-04-05
I would also suggest using ssh-server, but definitely suggest that you use it without passwords.

Here's the Ubuntu info on ssh, probably very similar to the link from The Cog.
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by sdsurfer on 2020-04-06
Is there any reason ***not*** to use Samba? Works great for my local network. Can access both my Linux computers and the Windows network for the Windows computers in the house.

---

### Post by The Cog on 2020-04-06
That's your first mention of Windows. Fine to use samba to share your Linux files to your Windows machines. But I would still recommend using ssh/sftp for LInux to Linux - it keeps all your file permissions and attributes.

---

### Post by Morbius1 on 2020-04-06
Why would you want to keep all your file permissions and attributes?

---

### Post by TheFu on 2020-04-06
> **Morbius1 said:**
> Why would you want to keep all your file permissions and attributes?

So they work on the other side?  On Unix systems, the data is only 50% of what we need.  Permissions are the other 50%.

Samba has all sorts of issues which can be easily avoided by using NFS or rsync or sftp.
Samba doesn't support the complete set of Unix file names.
Samba doesn't support owner, group, permissions.

These are bad things to lose.

---

### Post by Morbius1 on 2020-04-06
Did anyone read the original post? Is everyone assuming that all these machines in his network are owned and operated by one user?

Anyhoo.... So I have a Linux box named ork. My username is mork.

I install the samba package.
*EDIT: Just to make it clear it's:* [highlight]sudo apt install samba[/highlight]

Then I create a public share of my ... well ... Public folder in /etc/samba/smb.conf:
```
[Public]
path = /home/mork/Public
guest ok = yes
read only = No
force user = mork
```
Then restart smbd ( sudo service smbd restart ).

When Mindy on her Linux box wants to add a file to that share she enters my address in the location bar of her file manager or Connect to Server:
```
smb://ork.local/Public
```
Shazbot, she can even create a bookmark to that location.

Whatever she adds to that share will be owned by mork on ork. Whatever she copies from the share will be owned by mindy.

Right now the OP is using USB sticks formatted in fat32 maybe NTFS so all the files will be owned by whoever mounts the device just like the samba share.

---

### Post by TheFu on 2020-04-06
NFS is easier than samba, by far.  Plus, it works for all users on the multiple systems concurrently, not just 1 at a time.  Mounts are systems-to-system, not user-to-system.  if you want user-to-system, use sshfs.

The end users don't need to know any magic locations or incantations with NFS.  Just mount the storage in the same location on all machines. Any program can see and use it.  No training needed. No funky "you have the wrong version" issues like with different samba/Windows devices.  it works with scripts, shells, GUis and doesn't care if you use KDE or Gnome or LXDE or any other DE.  There's no magical addon that must be installed for Nautilus or Nemo or Caja or Thunar to work.  To every program on the system, NFS looks like local storage.

---

### Post by Gregory.Opera on 2020-04-08
> **The Cog said:**
> I would recommend using sftp. Install  openssh-server on the computers you want to connect to, then use your  normal file manager as the client (probably nautilus, but as I'm on  xubuntu I use its default file manager thunar). To connect to another  machine switch to a typed location (as opposed to buttons) and enter  something like "sftp://username@ipaddress". Then you can drag and drop  between that remote machine and local file manager windows. Picture  attached.[ATTACH=CONFIG]285405[/ATTACH]

You may also want to look at password-less logins: [https://www.linuxbabe.com/linux-server/setup-passwordless-ssh-login](https://www.linuxbabe.com/linux-server/setup-passwordless-ssh-login)


This looks like the way to go... Gonna have a play around with this tomorrow, see how it works out.


> **Autodave said:**
> *Teamviewer* is another option.

Probably not what I am looking for... But I will *definitely* have a  look at this, as there are *other* uses I might have for TeamViewer.

I  actually did not know TeamViewer was available for *Linux-based  operating systems*... Always thought it was just a Microsoft  Windows/Apple macOS thing.


> **The Cog said:**
> That's  your first mention of Windows. Fine to use samba to share your Linux  files to your Windows machines. But I would still recommend using  ssh/sftp for LInux to Linux - it keeps all your file permissions and  attributes.

Yeah, we're just a Linux household. Admittedly, the kids *do* have  Apple computers for school... But once they've finished school, they'll  go back to Ubuntu - Australia is *especially* anti-Linux and when I used  to run their computers on Ubuntu, it used to take up an *extraordinary*  amount of my time *getting* and *keeping* things working with the Microsoft  Windows / Apple macOS setups at schools (I was in the military at the  time too, so everytime we moved, _I'd need to start all over again_).

And  I can't wait - we paid an _incredible_ amount of money for multiple Apple computers,  which have *always* had half the performance *and* half the build quality as  our cheap-ish Linux laptops (Apple's customer service is top-notch, though!)... But I digress.

---

### Post by slickymaster on 2020-04-08
Thread moved to **Networking & Wireless** for a better fit

---

### Post by Morbius1 on 2020-04-08
> **Gregory.Opera said:**
> Admittedly, the kids *do* have  Apple computers for school... 
When you install samba on the Linux box it will automatically show up on the side panel of Finder. MacOS has defaulted to using samba since Mavericks first with the same samba we used then with their own rewrite ( smbx ),

And you can always use the same Connect to Server in MacOS with the same syntax: [highlight]smb://ork.local/public[/highlight]

---

### Post by TheFu on 2020-04-08
A Mac is mostly Unix, if you forget the GUI and their love to rename common things to "Apple-isms".  
NFS: [https://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/](https://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/)

---

### Post by Gregory.Opera on 2020-04-18
> **The Cog said:**
> I would recommend using sftp. Install  openssh-server on the computers you want to connect to, then use your  normal file manager as the client (probably nautilus, but as I'm on  xubuntu I use its default file manager thunar). To connect to another  machine switch to a typed location (as opposed to buttons) and enter  something like "sftp://username@ipaddress". Then you can drag and drop  between that remote machine and local file manager windows. Picture  attached.[ATTACH=CONFIG]285405[/ATTACH]

Interestingly,  I could _not_ get this to work Linux Mint-->Linux Mint (it just kept  timing-out *every* time), but I _could_ get it to work Linux  Mint-->Ubuntu using the same steps; in fact it not *only* worked *flawlessly* Linux  Mint-->Ubuntu, but it did so _the very first time_.

Of course,  next week *all* my computers will be going back to Ubuntu, so *hopefully* it  works just as seamlessly under Ubuntu 20.04 LTS, because this solution  was _*exactly*_ what I need to solve my problem.

Thanks!

---

### Post by TheFu on 2020-04-18
Perhaps Mint doesn't install the base ssh client packages?  If those are there, it should just work as a client. I don't use Mint, so I don't know.
Appears from this link: [https://snapcraft.io/install/sftpclient/mint](https://snapcraft.io/install/sftpclient/mint) that Mint is getting Snaps, which break all sorts of things due to aggressive file access constraints.  If you have an sftp terminal command and it isn't in a snap, then it should work as a client.  For the server-side, there just needs to be openssh-server, which includes the sftp-server tool automatically.  On a LAN, that should be sufficient.  I install both the ssh client and the server on all my systems. It is just to handy NOT to have. While I'm there I also install a brute force attack prevention IDS called fail2ban.

```
$ sudo apt install openssh fail2ban
```

That's it. No configuration of either should be needed.  File managers should work as an sftp:// client and the server should be running, protected by fail2ban, just after the install.  This should work the same on any Debian based system - Ubuntu, Mint included. If it doesn't, try installing these:
```
$ sudo apt install  fail2ban openssh-client openssh-server openssh-sftp-server
```
and avoid any snap package versions of any of those.

---

