---
title: "Help download ubuntu by splitting iso"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by edajai on 2009-10-23
my educational institute prevents download of large files. Is there any way that i can split the ubuntu iso (should be able to do it online) to 20 mb files so that i can download them and combine them later in my computer.

---

### Post by undecim on 2009-10-23
try the bittorrent option. Most bittorrent clients will let you download at a set maximum speed, and if the download gets stopped, it saves the parts that have downloaded and will pick up where it left off: 
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

If you are on a windows machine, I recommend using µtorrent to use the .torrent file: [http://www.utorrent.com/](http://www.utorrent.com/)

EDIT: If your education institution also blocks torrents, you can order free CDs: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by vinutux on 2009-10-23
> **undecim said:**
> try the bittorrent option. Most bittorrent clients will let you download at a set maximum speed, and if the download gets stopped, it saves the parts that have downloaded and will pick up where it left off: 
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

+1

---

### Post by SuperSonic4 on 2009-10-23
You can use wget with the -c option to download from where you left off previously

---

### Post by edajai on 2009-10-23
wget wont even start downloading the file since files >20 mb is blocked in our campus. Torrents are also blocked. Shipit takes a lot of time (2-3 weeks) :(

---

### Post by undecim on 2009-10-23
tell you what:

I'll download the ISO, split it up for you, and stick it on a website of mine... You want the i386 Desktop Edition (i.e. the default download)?

---

### Post by Mighty_Joe on 2009-10-23
The [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") is between 5 and 20Mb.  It's a text based installer that downloads all the packages from the net.

---

### Post by vinutux on 2009-10-23
> **undecim said:**
> tell you what:

I'll download the ISO, split it up for you, and stick it on a website of mine... You want the i386 Desktop Edition (i.e. the default download)?

mm.......rapidshare like serviec or rar parts...

Anyway only working solution for him

---

### Post by edajai on 2009-10-23
> **undecim said:**
> tell you what:

I'll download the ISO, split it up for you, and stick it on a website of mine... You want the i386 Desktop Edition (i.e. the default download)?
wow thaanks...
 desktop i386 for karmic (RC) will do.
n files below 20 mb pls... i still cant believe u would do this for me.. thanks again.

Rapidshare also blocked (i know, internet here sucks).

---

### Post by undecim on 2009-10-23
> **Mighty_Joe said:**
> The [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") is between 5 and 20Mb.  It's a text based installer that downloads all the packages from the net.
+1
I completely forgot about the minimal install CD! That would definitely be the best solution. As far as I know, aside from some game data packages, there are no packages greater than 20 mb to download.

And even then it is through https, right? so the file size thing might not even be enforceable (assuming this place isn't like my high school, which blocked https)

---

### Post by undecim on 2009-10-23
> **edajai said:**
> wow thaanks...
 desktop i386 for karmic (RC) will do.
n files below 20 mb pls... i still cant believe u would do this for me.. thanks again.

Rapidshare also blocked (i know, internet here sucks).

K, give me about an hour to split and upload it, and I'll post a link to it.

Though since it was mentioned, that minimal install may be easier for you, if you don't mind the terminal interface

Tell me which one you want to do, so I know if I have to upload the pieces

---

### Post by edajai on 2009-10-23
> **undecim said:**
> +1
I completely forgot about the minimal install CD! That would definitely be the best solution. As far as I know, aside from some game data packages, there are no packages greater than 20 mb to download.

And even then it is through https, right? so the file size thing might not even be enforceable (assuming this place isn't like my high school, which blocked https)
the kernel is >20 mb. Also i cant find a link to the minimal CD for karmic.
btw: https isn't blocked here.

---

### Post by undecim on 2009-10-23
> **edajai said:**
> the kernel is >20 mb. Also i cant find a link to the minimal CD for karmic.
btw: https isn't blocked here.

Something just occured to me: Are you trying to upgrade to karmic from jaunty? If so, you should be able to use update-manager -d (unless you need to reformat from to go from ext3 to ext4)

also with https enabled, you should be able to bypass that 20MB download limit by using https instead of http (since the blocking software they are using won't be able to tell how large a file will be) or at least use the wget -c (put it in a bash loop!)

or use encryption on your torrents (this would be the absolute fastest way to get it)

---

### Post by OpenGuard on 2009-10-23
> **edajai said:**
> the kernel is >20 mb. Also i cant find a link to the minimal CD for karmic.
btw: https isn't blocked here.

[HERE]("http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso") it is ..

---

### Post by edajai on 2009-10-23
@undecim
Please do upload the split files. As i'll be installing the combined iso in some of my friend's laptops also, minimal CD installation will take a hell lot of time (with the bandwidth available here)
Ubuntu Karmic RC i386
thanks again :D

---

### Post by undecim on 2009-10-23
K, I'm downloading it via bittorrent right now (its actually quite a wonder that I haven't already downloaded it myself)

Just to be safe, I'll split it into 20,000,000 - 1 B, instead of 20MB, which technically is 20,971,520 B

Just in case they configured the filters to block anything => 20 million bytes

---

### Post by jeremyswalker on 2009-10-23
You could also use jigdo to download the text-based installer. It downloads the needed files one-by-one, then assembles the CD image.

---

### Post by edajai on 2009-10-23
> **jeremyswalker said:**
> You could also use jigdo to download the text-based installer. It downloads the needed files one-by-one, then assembles the CD image.
but the kernel deb is around 25 mb and hence the jigdo method as well as updating from jaunty to karmic wont work

---

### Post by undecim on 2009-10-23
yikes... upload is going at 20kbps

I wish my server was still working... Then you could just download straight from my internet connection... (and it would be a lot faster than 20kbps!)

---

### Post by undecim on 2009-10-23
well, I have to go out now (an hour earlier than I was expecting)...

I'm really sorry I couldn't get it set up yet, but if you haven't gotten anywhere by the time I'm back  (I will be back home in about 5 hours), I'll finish setting it up.

---

### Post by undecim on 2009-10-23
Actually, I just set up lighttpd on my laptop, so you should be able to get to the files at [http://rissler.us.to/](http://rissler.us.to/) (they're being copied now)

I'll be removing those when I get home though, so that no one leeches my bandwidth XD

Remember to verify the final .iso with md5.```
undecim@caffeine:~$ md5sum ubusplit/ubuntu-9.10-rc-desktop-i386.iso
f9b1bfa64bdbd86f42b51d0cb6fa0cde  ubusplit/ubuntu-9.10-rc-desktop-i386.iso
```g2g... Good Luck!

EDIT: Back home now... access.log shows no downloaded it all yet, so I'll leave it up still.

A few hints that I didn't have time to post earlier:

You can download each of them consecutively with this command:```
wget -r http://rissler.us.to/
```

Once you have them, visit the folder that has the files (should download to ./rissler.us.to/) and use cat to put them together.```
cd rissler.us.to
cat ubuntu-9.10-rc-desktop-i386.iso.* > ubuntu-9.10-rc-desktop-i386.iso
```

And finally, make sure everything went right: ```
wget -O - http://releases.ubuntu.com/9.10/MD5SUMS | grep ubuntu-9.10-rc-desktop-i386.iso > MD5SUMS
md5sum -c MD5SUMS 
```If md5sum says that the file passed, then congrats. You have successfully downloaded the 9.10 RC.

---

### Post by edajai on 2009-10-25
i've downloaded just 20 files (in a random order). Plz keep the files online for one more day. I'll post here once i'm done.
Thanks

---

### Post by undecim on 2009-10-25
Well, Im in the middle of hardware issues (I think my hard drive might be going out! Im in a LiveCD backing up data right now)

And the fact that both my home server and the backup hardware I had for that server have failed... I'm beginning to wonder if I've angered the hardware gods or something.

Anyways, once I get this worked out, I'll get the files back up. Though since this is on a laptop that I take with me to classes, it won't be up during part of the day.

---

### Post by mangurt on 2009-10-25
Yicks!  That's not good.  How about downloading it via newsgroups?  Check and see if the uni blocks newsgroups (most don't), and you could probably grab it off of that.

---

### Post by undecim on 2009-10-25
Seems that it was just a corrupt filesystem. (caused by a bad shutdown?)

Pieces are back up, but I need to restart soon, so don't panic if it goes out for a minute

---

### Post by edajai on 2009-10-26
Thanks... finished downloading..
Going to install karmic now.
Thank you @undecim

---

### Post by 3rdalbum on 2009-10-26
It's incredible that someone went to those lengths to help you :-)  Well done.  If I'd been in that situation, I would have bought a disc off eBay and it would have arrived within a week.

---

### Post by revanb on 2009-10-26
Often educational institutes have ftp server and mirrors with ubuntu on them, so you could get it locally possible? Worth checking...

---

### Post by vinutux on 2009-10-26
undecim Done a gr8 job...........:)

This is called **[COLOR="DarkOrange"]die hard ubuntuism [/COLOR]** :P
:guitar:

---

### Post by woaiwojia on 2009-10-26
It's incredible

all of you are warm-hearted.

---

### Post by undecim on 2009-10-26
> **edajai said:**
> Thanks... finished downloading..
Going to install karmic now.
Thank you @undecim
No problem.

Btw, If you find that you can't upgrade the kernel packages, feel free to contact. If you want I can set up a script to automatically download and split updates. (Once I get my real server running again, that is.)

Though I think if you could configure your package manager to use https, the download couldn't be blocked. The filter won't be able to tell in advance how large the file is. Even if it cut the connection at 20MB, you can use wget -c with https.

Also, be sure to share the iso with anyone else under that 20MB restriction who needs it.

---

### Post by edajai on 2009-10-27
3 of my frnds hav already installed karmic frm ur iso.

How do i enable https connections for my package manager?

---

