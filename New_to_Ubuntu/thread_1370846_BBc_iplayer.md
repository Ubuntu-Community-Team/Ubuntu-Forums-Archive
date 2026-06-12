---
title: "BBc iplayer"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by nifty542 on 2010-01-02
Hi, all

I am having huge problems trying to get BBC iplayer to work. Non:(e of the links I have googled so far have worked. I have of course followed the bbc links. Any suggestions, please, friends?

---

### Post by laidback on 2010-01-02
I have it working on my system. I did have an initial problem that was solved by removing:-

swfdec-mozilla
and
Gnashxxx

via Synaptic. Other threads gave me the info. on this. The problem is with Flash, I had v10 loaded but FF just couldn't see it, instead reverting to the previous version which I think was 9 (I kept getting a message saying please load v10, but I had). After applying the above all was well. You can see what plugins you have be using FF and typing "about colon plugins" in the address bar. (use the character : )

Apart from that I think I just pressed the buttons on the BBC site to view the programme.

However, on a friends machine, running 9.04 as well, I did need to search the forum for other (additional) ideas which worked, but I'm afraid I don't have any references for that. 

Do post to let me know how you get on. I also believe that you need to be in the UK but I cannot swear to that.

---

### Post by Paqman on 2010-01-02
Are you trying to watch Flash videos on the iPlayer site, or are you trying to install the iPlayer Downloader?

---

### Post by kevinatkins on 2010-01-02
Yes, you need pukka Adobe Flash for iPlayer to work..

---

### Post by garryknight on 2010-01-02
> **kevinatkins said:**
> Yes, you need pukka Adobe Flash for iPlayer to work..

Or you could just install get-iplayer then download the programmes as .mp4 or .mov and watch them with something like vlc. If you have a British television license, that is...

---

### Post by laidback on 2010-01-03
Documentation for get-iplayer is here:-

[http://linuxcentre.net/getiplayer/documentation](http://linuxcentre.net/getiplayer/documentation)

Happy New Year

---

### Post by garryknight on 2010-01-03
That documentation is far too complicated.

Get a current listing of what's available, save it in home directory
get-iplayer >~/iplayer-listing.txt

Having found some interesting progs and noted the numbers in the left-hand column, download them:
get-iplayer --get 123 537

Get them with subtitles because I want to watch them very late at night with the volume down:
get-iplayer --subtitles --get 123 537

The first 2 commands probably cover more than 90% of users' needs.

---

### Post by lotharmat on 2010-01-03
> **garryknight said:**
> that documentation is far too complicated.

Get a current listing of what's available, save it in home directory
get-iplayer >~/iplayer-listing.txt

having found some interesting progs and noted the numbers in the left-hand column, download them:
Get-iplayer --get 123 537

get them with subtitles because i want to watch them very late at night with the volume down:
Get-iplayer --subtitles --get 123 537

the first 2 commands probably cover more than 90% of users' needs.

+1

---

### Post by benerivo on 2010-01-03
> **garryknight said:**
> Or you could just install get-iplayer then download the programmes as .mp4 or .mov and watch them with something like vlc. If you have a British television license, that is...

In the UK you don't need a tv licence if you don't watch live tv (ie. watch programmes as they are broadcast). Use of on-demand services such as bbc iplayer is exempt (see <http://en.wikipedia.org/wiki/Television_licensing_in_the_United_Kingdom> for more info).

Also, get-iplayer is great.

---

### Post by Paqman on 2010-01-03
Folks, I think we're in danger of veering off-topic here.

Are you still having trouble using the iPlayer, nifty542?

---

### Post by nifty542 on 2010-01-03
Hi, all
First of all, thanks for the many replies.I really appreciate it. Yes, I am still having trouble. The BBC fixes don't seem to work. Sorry I haven't replied earlier, holidays and alcohol, I guess, sorry. I don't need to install adobe air, just need streaming. 
Main reason I am on here, I am close to wanting to lose Windows just need this and Yahoo messenger to work, and I am gone

Thanks Friends all

Nifty

---

### Post by Paqman on 2010-01-03
What are the specs of your machine, and what type of Flash are you using? Are you using 32-bit or 64-bit?

In short: 
Don't use swfdec or gnash
If you're using 64-bit, use the native 64-bit Flash available from Adobe directly.

---

### Post by nifty542 on 2010-01-04
Hi, all

Thanks again. 
Specs: AMD 3200 (early 64 bit); 2gb 3200 ram. ATI Radeon 512mb (AGP). Running a wired network through a netgear router.

Thanks, all. 

Nifty

---

### Post by nifty542 on 2010-01-04
Hi

Well don't appear to have swfdec-mozilla and Gnashxxx installed in Synaptic. Downloaded the appropriate Flashplayer, but then got an error message- couldn't find plugin.

Want to tread carefully so I don't break my system, though I know it's easy to reinstall- but backing up is so tedious.

Thanks all

Nifty

---

### Post by nifty542 on 2010-01-04
Hi, all

Searched and got the following:

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

Also has link (broken) message for the link

Regards

Nifty

---

### Post by plucky on 2010-01-04
> **nifty542 said:**
> Hi, all

Thanks again. 
Specs: AMD 3200 (early 64 bit); 2gb 3200 ram. ATI Radeon 512mb (AGP). Running a wired network through a netgear router.

Thanks, all. 

Nifty

Your m/c might be early 64-bit,but are you running 64-bit software or 32-bit software?

From a terminal post output of ```
uname -a
```

---

### Post by nifty542 on 2010-01-06
Hi

Thanks again. Am running 64 bit.

As far as I can see, I have followed all instruction, but can't get flash to work, and when I click on play or download, the icone just spins a few times and returns.

Regards

Nifty

---

### Post by philinux on 2010-01-06
> **nifty542 said:**
> Hi

Thanks again. Am running 64 bit.

As far as I can see, I have followed all instruction, but can't get flash to work, and when I click on play or download, the icone just spins a few times and returns.

Regards

Nifty

```
sudo apt-get purge flashplugin-nonfree
```

Now get the 64 bit plugin from adobe, download to desktop.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Right click when downloaded and select extract here.

Inside the folder will be the 64 bit libflashplayer.so.

Copy or move this to /home/youruser/.mozilla/plugins
You'll have to create the plugins folder first.

Restart firefox.

---

### Post by nifty542 on 2010-01-07
Hi, Phil.

Thanks for the reply. Did that, but now the programme page won't load properly- it just displays a white oblong where the image should be.
Would love to get this to work.

---

### Post by nifty542 on 2010-01-07
Hi
Quote Or you could just install get-iplayer then download the programmes as .mp4 or .mov and watch them with something like vlc. If you have a British television license, that is.

Sorry, missed that bit. How would I do that?

Regards

Nifty

---

### Post by Greenwidth on 2010-01-07
It's CLI (runs from terminal) although there are some GUI's for it I haven't tried them.

get_iplayer download:
[http://linuxcentre.net/getiplayer/download](http://linuxcentre.net/getiplayer/download)

documentation:
[http://linuxcentre.net/getiplayer/documentation](http://linuxcentre.net/getiplayer/documentation)

---

### Post by nifty542 on 2010-01-07
Hi, all

Many many thanks to all of you who have helped. I just tried a restartand it's working! So I can rewatch Dr Who, now.........

Thanks a lot

Regards

Nifty:)

---

### Post by nifty542 on 2010-01-07
Hi, all

Well, spoke too soon. Clicked on another programme, and it's back to exactly the same problem- click on play or download and nothing happens

Oh well...

Nifty:(

---

### Post by Greenwidth on 2010-01-07
Fix for 64 bit Flash:
[http://ubuntuforums.org/showthread.php?t=1319541](http://ubuntuforums.org/showthread.php?t=1319541)

---

### Post by garryknight on 2010-01-07
> **nifty542 said:**
> Hi
[quote=garryknight] Or you could just install get-iplayer then download the programmes as .mp4 or .mov and watch them with something like vlc. If you have a British television license, that is.

Sorry, missed that bit. How would I do that?

Regards

[/quote]


What, get a British TV license? :) Just kidding.

You can install get-iplayer using Synaptic (in the Universe repo under Video). Or you can install it from the command line with "apt-get get-iplayer".

It's a command-line app but it's extremely simple to use:

# get a listing of what's available on the iPlayer site, store in home directory
get-iplayer >~/iplayer-listing.txt

When you find the program you want to download, make a note of the number in the left-hand column, then feed it to "get-iplayer --get":

# download a couple of videos
get-iplayer --get 195 573

# download a video with subtitles so I can watch late at night with the volume down
get-iplayer --subtitles --get 407

(Note that not all videos come with subtitles.)

You can watch them in anything that supports .mp4, .mov, and .flv. I use vlc.

---

### Post by johnaaronrose on 2011-08-08
I've written a simple GUI (calling get_iplayer) allowing recording of a selected TV/radio programme. It's in Gambas. Its .deb package (which includes Gambas runtime) is downloadable from:
[http://dl.dropbox.com/u/3928731/irecorder_0.0.37-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0.37-1_all.deb)

However, get_iplayer 2.78 now refuses to work for me - it stops after 60/90 MB. rtmpdump  v2.3 & flvstreamer 1.9 are installed. Has anyone else had this problem? Only thing that I can think is that get_iplayer will only work for a specific mode e.g. iphone.

---

### Post by ron999 on 2011-08-08
> **johnaaronrose said:**
> 
However, get_iplayer 2.78 now refuses to work for me ...
Hi
The get_iplayer script is now at v2.79.

This command will update it for you if you like:-

```
sudo apt-get install git-core && \
cd ~/ && \
git clone git://git.infradead.org/get_iplayer.git && \
sudo cp ~/get_iplayer/get_iplayer /usr/bin/get_iplayer

```
Then you can use this command to check it's updated:-
    ```
ls -lh /usr/bin | grep -i "get_iplayer"
```

> ron@ubuntu:~$ ls -lh /usr/bin | grep -i "get_iplayer"
-rwxr-xr-x 1 root   root     335K [COLOR="Red"]2011-08-08 15:10[/COLOR] get_iplayer
lrwxrwxrwx 1 root   root       11 2011-08-06 12:32 get-iplayer -> get_iplayer

---

### Post by johnaaronrose on 2011-08-09
Thanks, ron999. However, change of version made no difference. I've figured out the cause. It's due to get_iplayer calling rtmpdump/flvstreamer: Gambas doesn't seem to support this calling of a CLI program by another CLI program.

So I've put in a --raw parameter when invoking get_iplayer from within the iRecorder app. Its .deb package (which includes Gambas runtime) is downloadable from:
[http://dl.dropbox.com/u/3928731/irecorder_0.0.39-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0.39-1_all.deb)

Selecting Default mode has resulted in TV programmes creating .flv files. Use Mobile Media Converter / HandBrake / VLC / WinFF if you wish to convert to another format (e.g. to play on the iphone). 

I'd be grateful if people who try iRecorder would let me know their experiences with it, particularly if they wish to suggest enhancements. 

I'd be happy to write similar functionality incorporated into iRecorder of the code used in get_iplayer if anyone could document the Perl code used by iRecorder (i.e usage of the search and get options. Alternatively, documentation of the requests & responses from the iPlayer archives. Similarly, for Channel 4 IOD.

---

### Post by johnaaronrose on 2011-08-10
Apologies, I've mislead everyone. The .deb file is Canonical's attempt at  packaging get)iplayer 2.79 which is actually 2.78! As ron999 previously said: to get get_iplayer  2.79, run following in terminal:
sudo apt-get install git-core && \
cd ~/ && \
git clone git://git.infradead.org/get_iplayer.git && \
sudo cp ~/get_iplayer/get_iplayer /usr/bin/get_iplayer
(which will put  the source etc into a new directory called get_iplayer, which you can  delete afterwards, as the Perl script is installed into /usr/bin)

Alternatively, get the Perl script from:
[http://dl.dropbox.com/u/3928731/get_iplayer](http://dl.dropbox.com/u/3928731/get_iplayer)
and install it by:
sudo mv /home/user/Downloads/get_iplayer /usr/bin/
(assuming that user is your login id & that you have configured  Firefox to download to Downloads directory, otherwise adjust  appropriately) .

---

### Post by johnaaronrose on 2012-07-09
Latest version of iRecorder is at:
[http://dl.dropbox.com/u/3928731/irecorder_0.0-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0-1_all.deb)

You need to use Gambas 3 ppa by kendek, due to Benoit now having a check
that Gambas version dev = (though might be <=) Gambas version run on. It downloads from:
[https://launchpad.net/~nemh/+archive/gambas3](https://launchpad.net/~nemh/+archive/gambas3)

No need to download anything explicitly from the ppa site: after adding  the repository, just do sudo apt-get update & sudo apt-get upgrade.  Running the above .deb should cause gdebi to install the appropriate  Gambas3 modules.

---

