---
title: "nautilus video thumbnails problem"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by Prescilla on 2011-07-10
Hello everyone. I am new to Ubuntu and I have recently noticed that all my video files cannot or will not display video thumbnails instead all video files as displayed with a video icon. I am using Ubuntu 11.04 and my video player is VLC. Can somebody help me please?

---

### Post by jtarin on 2011-07-10
Do you have libxine1-ffmpeg installed? That may be needed for some thumbnails.
Try
```
sudo apt-get install libxine1-ffmpeg
```

Then to force nautilus to generate new thumbnails by executing.

```
rm -r $HOME/.thumbnails/fail
rm -r $HOME/.thumbnails/normal
killall -9 nautilus
```These commands will remove (delete) thumbnails from these folders.

---

### Post by horton4483 on 2011-07-11
I didn't ask the ? but i was searching for an answer. I wanted to say thank you for the info, it worked perfectly for me. I'm still an ubuntu noob but in time hopefully i will be able to answer ? for those in need as well. :)

---

### Post by jtarin on 2011-07-11
> **horton4483 said:**
> I didn't ask the ? but i was searching for an answer. I wanted to say thank you for the info, it worked perfectly for me. I'm still an ubuntu noob but in time hopefully i will be able to answer ? for those in need as well. :)@horton4483...your welcome...glad to help.

---

### Post by Prescilla on 2011-07-14
I did as per instructions:

prescilla@prescilla:~$ sudo apt-get install libxine1-ffmpeg
[sudo] password for prescilla: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-ffmpeg is already the newest version.
The following package was automatically installed and is no longer required:
  libcrypto++8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
prescilla@prescilla:~$ rm -r $HOME/.thumbnails/fail
prescilla@prescilla:~$ rm -r $HOME/.thumbnails/normal
prescilla@prescilla:~$ killall -9 nautilus
prescilla@prescilla:~$ 

still my videos does not display in thumbnails :((

---

### Post by sroland81 on 2012-03-26
The same happens to me in Ubuntu Precise 12.04 beta 1, installed libxine1-ffmpeg but it did not solve the problem.

I can see that the issue is with some mp4 videos

any ideas?

---

### Post by sinaphysics on 2012-04-05
@[jtarin]("http://ubuntuforums.org/member.php?u=738123") about post #4
It works perfect.

---

### Post by orlando.terte on 2012-05-19
Nautilus Ubuntu Missing Thumbnails
The thumbnails in Nautilus do not seem to be regenerated, once the correct libraries or codecs for different video formats are installed. If one has opened the folder filled with videos without installing codecs, there's a chance they have been blacklisted by the thumbnailer. 

The solution is to open the /home/[username]/.thumbnails folder and delete all files in fail folder.

After that, to restart Nautilus from a command line, do:
>killall nautilus

>nautilus &

Now it should regenerate the thumbnails. 

If this does not work, please make sure you are able to play those videos, and correct libraries to play them are installed.

You can also try deleting all files in the all folders in.thumbnails.

courtesy of [http://fixed-it.blogspot.com/2009/08/nautilus-ubuntu-missing-thumbnails.html](http://fixed-it.blogspot.com/2009/08/nautilus-ubuntu-missing-thumbnails.html)

---

### Post by DIOGYK on 2012-07-23
I have ubuntu 12.04 LTS, I tried what jtarin said, but my video thumbnails aren't generating again, any solutions?
thanks.

---

### Post by goanna300 on 2012-09-14
Nope, me neither.

How come this thread is marked as solved?

---

### Post by GouZi on 2012-09-21
The solution mentioned in that thread did not work for me, on 12.04.
You need to install more codecs (depending upon the kind of videos you have).

The following worked for me:
```

sudo apt-get install libxine1-ffmpeg
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly totem
sudo apt-get install ubuntu-restricted-extras
sudo rm -r $HOME/.thumbnails/fail
sudo rm -r $HOME/.thumbnails/normal

```

---

### Post by oldos2er on 2012-09-21
Old thread closed. Anyone still having this problem, please start a new thread.

---

