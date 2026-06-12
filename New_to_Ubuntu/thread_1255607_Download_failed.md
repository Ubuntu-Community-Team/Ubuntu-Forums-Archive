---
title: "Download failed"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by Miscible21 on 2009-09-01
Im so bleek. I tried to download ubuntu 8.04 and it failed at 62%. I only get 1 gig of bandwidth a month. thats not much. I have resumed the download but from experience i know the files are sometimes damaged when the download is broken. I doubt I can start a completely new download again. What should I do now? complete the download and see if it works or should I stop it, clear my history and start a new one when i have more bandwidth?

---

### Post by ks07 on 2009-09-01
> **Miscible21 said:**
> Im so bleek. I tried to download ubuntu 8.04 and it failed at 62%. I only get 1 gig of bandwidth a month. thats not much. I have resumed the download but from experience i know the files are sometimes damaged when the download is broken. I doubt I can start a completely new download again. What should I do now? complete the download and see if it works or should I stop it, clear my history and start a new one when i have more bandwidth?
I would complete the download, then check if it is corrupted or not by checking the md5sum of the .iso file.

[Read this page (the section entitled "Checksum")]("http://www.psychocats.net/ubuntu/iso#checksum")

You will need to download and install WinMD5Sum from the link at the top of the page in windows to carry out the check.

---

### Post by lhb1142 on 2009-09-01
What have you got to lose by continuing the download? You are already at 62% so you should be able to get the rest easily. If it works, and it probably will, great. If not, you are no worse off than if you had deleted what you had and started all over again.

> **Miscible21 said:**
> Im so bleek. I tried to download ubuntu 8.04 and it failed at 62%. I only get 1 gig of bandwidth a month. thats not much. I have resumed the download but from experience i know the files are sometimes damaged when the download is broken. I doubt I can start a completely new download again. What should I do now? complete the download and see if it works or should I stop it, clear my history and start a new one when i have more bandwidth?

---

### Post by Garrovick on 2009-09-01
You could always simply buy a disk.

[http://www.ubuntu.com/getubuntu]("http://www.ubuntu.com/getubuntu")

I am going off line for almost a year, so I'll most likely order the DVD.

---

### Post by tgeer43 on 2009-09-01
That's really up to you but I think there's a pretty fair chance that the file will be intact after the download completes.

You can buy Ubuntu on CD/DVD for only $12.00 US from Amazon.com:

[http://www.amazon.com/gp/product/3937514775?ie=UTF8&tag=ubuntusearch-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=3937514775](http://www.amazon.com/gp/product/3937514775?ie=UTF8&tag=ubuntusearch-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=3937514775)

Or if you are not in a particular hurry you can order a free Ubuntu CD from Canonical (6-10 week delivery):

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Boy, that's a really crappy plan you have - only 1GB/month?
I would burn through that in the first 30 minutes.

tgeer

---

### Post by Miscible21 on 2009-09-01
> **tgeer43 said:**
> That's really up to you but I think there's a pretty fair chance that the file will be intact after the download completes.

You can buy Ubuntu on CD/DVD for only $12.00 US from Amazon.com:

[http://www.amazon.com/gp/product/3937514775?ie=UTF8&tag=ubuntusearch-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=3937514775](http://www.amazon.com/gp/product/3937514775?ie=UTF8&tag=ubuntusearch-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=3937514775)

Or if you are not in a particular hurry you can order a free Ubuntu CD from Canonical (6-10 week delivery):

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Boy, that's a really crappy plan you have - only 1GB/month?
I would burn through that in the first 30 minutes.

tgeer
It is a shitty plan. but in South Africa we get the really really short end of the stick with service providers. Internet is quite pricey if you want a fast connection. my connection is fast but my cap is small. I may upgrade but it would probably be better to change service providers. So trust me, i could go through a gig in 30 minutes as well, but you eventually have to learn some self restraint lol

---

### Post by Miscible21 on 2009-09-01
> **ks07 said:**
> I would complete the download, then check if it is corrupted or not by checking the md5sum of the .iso file.

[Read this page (the section entitled "Checksum")]("http://www.psychocats.net/ubuntu/iso#checksum")

You will need to download and install WinMD5Sum from the link at the top of the page in windows to carry out the check.
ks07, im having trouble downloading MD5. it somehow downloads as an exe folder, which is clearly not the full application. its the same with infra recorder

---

### Post by mprince on 2009-09-01
Consider downloading the 8.04 torrent and then use the partial 62% file as the starting point. The torrent application should weed out any damaged chunks on a Verify data check... and then just continue to download the remainder of the file as a torrent.

---

### Post by Miscible21 on 2009-09-01
> **mprince said:**
> Consider downloading the 8.04 torrent and then use the partial 62% file as the starting point. The torrent application should weed out any damaged chunks on a Verify data check... and then just continue to download the remainder of the file as a torrent.
mprince, i think thats a great idea, it would probably work. However, my download is already finished so i cant do that. but im gona do a checksum and see if it worked out.

---

### Post by mprince on 2009-09-01
You can do an md5sum using terminal.

```
md5sum path/to/filename
```

---

### Post by Miscible21 on 2009-09-01
just did the checksum thing with MD5. It says the checksums dont match. Am i screwed?:-k

---

### Post by mprince on 2009-09-01
Double check that you've got the right checksum for the version of ubuntu you are downloading. 32bit, 64bit, server, alternative versions all have different checksums.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

As a last resort you could still download the 8.04 torrent and have it do a check on the file you've downloaded. It should weed out any corrupted chunks and re-download just those bits. The torrent app won't care that the file is at 100%

---

### Post by ks07 on 2009-09-03
> **Miscible21 said:**
> ks07, im having trouble downloading MD5. it somehow downloads as an exe folder, which is clearly not the full application. its the same with infra recorder
Oh sorry, I'm guessing then that you are downloading from ubuntu/another linux distro. I presumed you were using windows. That guide is written for Windows users lol. :P

Like mprince said, make very sure that you are comparing the right MD5 hashes.

[QUOTE=mprince]As a last resort you could still download the 8.04 torrent and have it do a check on the file you've downloaded. It should weed out any corrupted chunks and re-download just those bits. The torrent app won't care that the file is at 100%[/QUOTE]

Hey great idea man, someone's on the ball lol. :)

---

### Post by mejohnsn on 2009-09-03
> **Miscible21 said:**
> just did the checksum thing with MD5. It says the checksums dont match. Am i screwed?:-k

Yes. By your ISP. Seriously. If you are paying that much for the bandwidth, and then your download attempts keep failing, then you are not getting what you are paying for.

But while you duke it out with your ISP, I have a couple suggestions that may provide more immediate relief.

1) assuming you still have access to some Unix system, use 'wget' instead of your web browser. As the man page for wget says,

> 
Wget has been designed for robustness over slow or unstable network
connections;

This sounds like just what you need. I usually use all the defaults, and then figure out where it put the file, then move it where I want it.

You could, for example, do:

wget [http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/hardy/release/ubuntu-8.04.1-dvd-i386.iso](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/hardy/release/ubuntu-8.04.1-dvd-i386.iso)

And wait... and wait...

2) another alternative is to use a P2P client. I chose Azureus a long time ago, I am not sure that it is still the best choice. That is how I downloaded Ubuntu 8.04.1, which I am running now. It too automatically retries until it gets it right. Sometimes, it is much faster.

---

### Post by dph on 2009-10-30
Yes,

I got an error message when I checked the ubuntu install disk for errors under the ubuntu primary install menu screen. I tried downloading from another site and got errors on the new disk as well. I think there is a bug in the ISO file somewhere.

---

### Post by 3rdalbum on 2009-10-30
Use Bittorrent - it downloads files in chunks and verifies hashes for each chunk, so you never get a damaged download, even if a peer shuts down or crashes in the middle of a chunk.

If you can't use Bittorrent, then at least use Wget; if the transfer fails, it will attempt to reconnect and resume download. If you have to turn off Wget, make sure to start it again with the "-c" option so it will continue where it left off.

---

