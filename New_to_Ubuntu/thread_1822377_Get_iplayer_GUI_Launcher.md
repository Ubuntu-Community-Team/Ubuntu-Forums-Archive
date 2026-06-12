---
title: "Get_iplayer GUI Launcher"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by mrdtb on 2011-08-10
Hi All

I'm completely new to linux. I installed ubuntu over the  weekend after my (hated) instal of Windows Vista failed massively and I  couldn't bring myself to even try and recover it :)

So far  installation is going well, got most things working and (I think) a grip  on the basics, thanks to all the help and developers out there &c. 

Anyway, to my question.

One of my most loved programs on Vista was Get_Iplayer, so obviously I wanted to get that up to spec as soon as possible. 

I've  installed the Get_Iplayer GUI and had the browser interface running in  firefox fine using the instructions here  [http://ubuntuforums.org/showthread.php?t=1658940](http://ubuntuforums.org/showthread.php?t=1658940) Thanks nothingspecial.

Which  is great, and I'm happy in general with the basic idea of using a  terminal. But you know I'm used to clicking little icons and stuff  happens, and I really can't keep long (to me) unintelligable pieces of  code in my head. 

So what I want to know is this. Is there a way  to simply(ish) wrap up those two pieces of script command line  or  whatever they are correctly called into a package that I can launch from  the Apps menu or desktop icon? Even better that will then launch the  GUI in a browser window. This was what you got in windows, and this was a  good thing. 

I'm running on Ubuntu 10.10 LTS

Many Thanks in advance

---

### Post by watford on 2011-09-04
I'll second that, couldn't have put it better myself. Is the reason you have now reply because the question is answered elsewhere ? Have you managed do this yourself maybe ?

---

### Post by johnaaronrose on 2011-09-27
I've written (in Gambas) a get_iplayer GUI for downloading (i.e. saving on disk) programmes. It comes as a .deb package which when you install it will automatically download Gambas runtime. It will automatically give you the option to download the .deb package when you click on the link below:
[http://dl.dropbox.com/u/3928731/irecorder_0.0.39-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0.39-1_all.deb)

Please let me know how you get on with it.

---

### Post by mrdtb on 2011-12-14
Hi
 
Just stumbled back on this post, which I'd given up hope on... 
 
I've managed to get the get_iplayer terminal to run using a launcher, I don't recall where I found instructions for this now, I think it was an Ubuntu Wiki sorry Watford. I'm having trouble getting the laucher to lauch the terminal then a invoke a firefox window, I think because the script doesn't progress once get_iplayer is running as this 'takes over' the terminal window. Anyway that is OK, as long as I don't have to keep typing into the terminal. 
 
johnaaronrose, I'll give you gui a go when I get a mo' and let you know what I think. I'm not sure when that might be mind.
 
Thanks for the help
 
mrdtb

---

### Post by spider_0k on 2012-01-16
I would love to give your GUI Launcher a go, but your link seems dead.
I have been looking for something like this for a long time.
Looking forward to good news.

Philip

---

### Post by johnaaronrose on 2012-01-17
Current .deb package for iRecorder GUI is:

[http://dl.dropbox.com/u/3928731/irecorder_0.0.46-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0.46-1_all.deb)

---

### Post by spider_0k on 2012-01-17
> **johnaaronrose said:**
> Current .deb package for iRecorder GUI is:

[http://dl.dropbox.com/u/3928731/irecorder_0.0.46-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0.46-1_all.deb)

Thanks for the update.

Philip

---

### Post by neigun on 2012-07-05
> **johnaaronrose said:**
> Current .deb package for iRecorder GUI is:

[http://dl.dropbox.com/u/3928731/irecorder_0.0.46-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0.46-1_all.deb)

The all deb link appears to be broken again.  Is the gui IRecorder still being maintained?

The reason I ask is that BBC iplayer does not want to play ball with 12.04 amd64 and I prefer a gui, though get-iplayer does the job.

Neil

---

### Post by johnaaronrose on 2012-07-07
Neil,

Latest version of iRecorder is at:
[http://dl.dropbox.com/u/3928731/irecorder_0.0-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0-1_all.deb)

You need to use Gambas 3 ppa by kendek, due to Benoit now having a check
that Gambas version dev = (though might be <=) Gambas version run on. It downloads from:
[https://launchpad.net/~nemh/+archive/gambas3]("https://launchpad.net/%7Enemh/+archive/gambas3")

No need to download anything from the ppa site: just do sudo apt-get update & sudo apt-get upgrade. Running the above .deb should cause gdebi to install the appropriate Gambas3 modules.

---

### Post by neigun on 2012-07-21
John

That has done the trick, though I did have to install the ppa in the end.  The quality of the downloads is far better than that streamed in to a browser. 

Is there anyway to get the other UK channels such as 4 & 5?  

The play function does not seem to work, in that a directory has to be selected for the log file and then it just does nothing.  Any suggestions?

Thanks

Neil

---

### Post by johnaaronrose on 2012-07-21
Neil,

iRecorder is purely a wrapper around get_iplayer. Therefore, it cannot do anything that get_iplayer cannot do e.g. access non-BBC channels (e.g. ITV, Channel 4, Channel 5). I don't understand get_iplayer's coding: the coding seems to me to be unnecessarily complex but I don't know PERL. I've seen on one of get_iplayer's websites a statement to the effect that the coding is a mess. I think it was one where the site's author said that they were writing an app called Prometheus to replace get_iplayer. AFAIK that never happened.
 
If anybody could find out details about the BBC's iPlayer feeds or point me to a web site containing its details, I'd incorporate the necessary Gambas coding (and not use get_iplayer) into iRecorder. That way iRecorder would be much more robust and I'd be able to debug it properly - at the moment I feel that I'm searching for needles in a haystack due to the vagaries of get_iplayer and the programs that it calls (e.g. I think that it calls rtmpdump).

Also, I'd be able to obtain more information from the BBC's feeds, e.g. date a specific programme first broadcast, to display in iRecorder's window. The same applies to being able to access non-BBC channels.

PS I'm not able to test iRecorder on Ubuntu Oneiric due to my dev PC & other machines all using Ubuntu Lucid (64 bit, 32 bit, netbook): I do not intend to move to Oneiric until next April (i.e. when Lucid support ceases) or to another distro (e.g. Linux Mint) as I only use Ubuntu LTS releases unless somebody provides a good reason why I should move sooner.

---

### Post by neigun on 2012-07-22
Hi John

I think I've read something about iplayer feeds; if I can find it again I shall post it here for you.

The original developer had proved it was possible, with plugins, to watch other channels via get-iplayer: [http://linuxcentre.net/get_iplayer-dropping-channel4-4od-demand-five-and-hulucom](http://linuxcentre.net/get_iplayer-dropping-channel4-4od-demand-five-and-hulucom)

but subsequently dropped the idea.

Your app works with iplayer v2.82 and on Precise with the exception of the play button.

Thanks again,

Neil

---

### Post by johnaaronrose on 2012-07-22
Neil,

I took a look at that URL you provided but it didn't help: sometimes I think that certain people take a perverse delight in making their comments (i.e. on that web site) unintelligible!

PS I should have referred to Precise not to Oneiric: age must be getting to me.

---

### Post by neigun on 2012-07-22
John,

Don't worry,we all have senior moments at times!

How do I get the play button working?

Regards,

Neil

---

### Post by johnaaronrose on 2012-07-23
Neil,

On Lucid, clicking the 'Play' button results in displaying a window asking in which directory to store the log file. After selecting the directory (for which you write permission) it opens a window in which MPlayer 'plays' the video stream. MPlayer uses package mplayer. I thought that it was part of the standard Ubuntu install but I could be wrong. Please check that you have the package installed on Precise.

---

### Post by neigun on 2012-07-23
John, 

For some reason Totem was installed by default, though I personally prefer to use VLC. However, I installed Mplayer and it worked first time.

Neil

---

