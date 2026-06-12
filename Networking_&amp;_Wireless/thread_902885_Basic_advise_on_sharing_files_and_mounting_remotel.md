---
title: "Basic advise on sharing files and mounting remotely..."
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by XtremeGamer99 on 2008-08-27
Hello,

First off -- warning: wall of text. There is no tl;dr version, so please stck me me. =) I have recently set up a home server to handle a variety of tasks, including a web server, database server, and file server. The file server part is the main purpose of this computer, since it will be hosting all my music, videos, and document that I need to share no matter which computer I'm on (I have three) or OS I'm using (in all, five).

I have my main computer running Debian Lenny w/ KDE, and has the option to boot into Windows XP for games and such. I have a laptop running Ubuntu w/ GNOME (duh), and it has the option to boot into Vista (not that I ever use it, but there are some programs). Then there's the family computer, which, of course, runs Windows XP.

The server has a second hard drive whose main purpose is the house the shared files. I have it mounted on /export/share, and whatever is on that partition gets shared. I have set up a Samba server (not a very well-configured one, but it works) to handle the file sharing for the Windows machines, and on the Windows machine I just have it mount the share as a network drive. Done. But I'm running into a bit of a road-block when it comes to overall security and mounting in Linux.

What would be the best way to mount the share in my Debian and Ubuntu? I would like it to be recognized as if I were to plug in a USB drive (eg: it pops up on the desktop).I was thinking NFS would do the trick, but where exactly would I mount it? Under /media? Under /import?

My other question is about security. How secure would it be to mount with just plain NFS with the Linux distros, and also with a minimal Samba config? It should also be noted that the only hardwired connection to the home network is my main computer and the server. The family computer and my laptop are wireless, and thus prone to interception. I don't think there's much I can do with Samba to encrypt it's transfered data unless it's able to do that without performance loss (it's a fairly old computer, the server), but I know that NFS can be encrypted somehow (with SSH, I think?). I know that its only music and junk that's being shared, but since it a writable share for everyone, I don't want anyone to be able to get into my network, find the share on a scan of available shares, and steal/erase data. Anyway to do this while still keeping convenience? Maybe it's just a matter of setting it to read-only, and requiring you to log into a user that has write access for it. I dunno.

Also, I don't want anyone trying to access shares through the internet, unless it's by me (I like to have my music from home at college >_>). I have a router that divides my network from the internet, but I just want to make sure that there isn't much anyone can do (who isn't very determined) to access them over the internet. I know I can by connecting to the server through SSH, and that's fine and dandy. I just don't want others to. >_>

So... yeah... Basically, what's the best way to to set-up and share/mount files from a server, securely, to Linux and Windows machines, while avoiding outside influence (guy next door with laptop/internet as a whole). Huh, I guess there is a tl;dr version. <_<

Thanks! =D

---

### Post by XtremeGamer99 on 2008-08-29
Anyone?

---

### Post by SpaceTeddy on 2008-08-31
the answer is: sshfs.

On the server, you have the openssh server running - that one is running anyway (as you need it for remote login) - so why not use it ? if you are using a linux client, install sshfs, add yourself to the fuse group and off you go.... sshfs username@server:/path/on/server localpath (i have a directory called remote in my homedir where i mount remote ssh shared. Works like a charm for me.
With windows, there is a little programm called [[COLOR="Blue"]sftpdrive[/COLOR]]("http://www.magnetk.com/sftpdrive/"). It's not free, but does the same thing as sshfs in windows... i have not found a better one yet (but i haven't been looking either as i use windows very... very rarely anymore)
Why this approach ? because it is simple. You have no configuration files, you have no server setup - you don't need to install much. As a Bonus, you can setup shared keys for ssh to have passwordless login, all traffic is encrypted by default and once your client can do this you can mount ANYTHING that has a openssh server runnning...

hope it helps :)

---

