---
title: "Torrent Programs and Moving to a Samba Drive?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by tazz131 on 2011-04-12
Hi, very new to Linux...

I'm currently using Ubuntu 11.04.

I've installed various Torrent clients, I'm currently back to uTorrent with Wine, but I can't do what I want with it, or any of the other programs I've tried.

The option is there to move completed files to a specific folder.  I want the files to move specifically to my NAS drive.

I can see the drive when I go to my home folder, but when I'm selecting the folder in the torrent program I do not have access to the network folder.

Is there any way to access my network drive from within a torrent program?

Thanks.

---

### Post by earthpigg on 2011-04-12
hi,

not sure i have a direct answer to your question, but i will share with you the standard approach:

run the torrent software on your NAS, and control it from your desktop. if your NAS is using Ubuntu, Transmission ought to do nicely. It has a web client, so you put the IP of your NAS in the web browser, and *poof* you are looking at the transmission user interface inside of your web browser or on your smartphone's web browser or whatever.

If your NAS is using something that does not include X (including ubuntu server), then you can use a ncurses-based .torrent client and ssh.

it is a much nicer and cleaner approach. alternatively, you can run Transmission on your desktop and have it download directly to your NAS - Transmission can see network folders.

---

### Post by tazz131 on 2011-04-12
Ya, that would be a good approach, however, the catch, which I should have added is that I like to use RSS feeds.

In my experience so far, it doesn't look like transmission uses rss feeds.  Is there a plugin?

Are there any torrent programs that use RSS feeds, like uTorrent does?

Is there a trick to allow Transmission to see my network, because I can't seem to figure it out.

---

### Post by earthpigg on 2011-04-12
if the network filesystem is mounted, it should show up in transmission...

```
df -Th
```

do you see your network folder? try navigating to it's "mounted on" manually, in transmission.

---

