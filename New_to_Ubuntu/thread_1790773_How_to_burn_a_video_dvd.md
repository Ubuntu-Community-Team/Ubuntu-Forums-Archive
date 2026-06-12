---
title: "How to burn a video dvd?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by nifty542 on 2011-06-25
Hi, all

I am trying to make a dvd from files downloaded from the net. Although Brasero can recognise the file it gives the message Please install the following manually and try again:mplex (GStreamer plugin). 
I can't find this in Synaptic. Can anyone offer any advice or point me to a link, please?

Regards
Nifty

---

### Post by josephmills on 2011-06-25
here you go get to medibuntu ing [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by nifty542 on 2011-06-25
Hi

Thanks. I'll give it a go

Regards
Nifty

---

### Post by nifty542 on 2011-06-25
Hi, all

Well, tried that and still get the same message! Any ideas, anyone?

Regards

Nifty

---

### Post by josephmills on 2011-06-25
[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

also make sure that all repos are open in software sources
also you want the non-free

---

### Post by pbpersson on 2011-06-25
Exactly what type of files are you starting with?

.MOV files?
.MPG files?

How are you attempting to convert them into a movie?

I have never used the software package you mentioned.

Have you looked at [DVDauthor]("http://dvdauthor.sourceforge.net/")?

I have never used it but I know it is in the repos

---

### Post by josephmills on 2011-06-25
brasero is the default burner for ubuntu and it is not going to burn anything until he gets the libs to run that codec


you could try opening synaptic type in gstreamer into the search bar  and make sure the good  and bad and ugly files are installed

---

### Post by nifty542 on 2011-06-25
Hi, all

The files are all MP4. I have tried to make a movie file using DeVeDe. It seems to convert them, but then I seem to go around in circles- it keeps converting and putting the file in my home directory.Then I get the message that the file already exists.
So, I thought I would try Brasero.
I have checked that gstreamer bad and ugly are installed- they have to be, according to the documentation, to play dvds. 
Many thanks for the replies- it is marvellous to be able to get help this way.
Regards
Nifty

---

### Post by SeijiSensei on 2011-06-25
So you get the .iso file from DeVeDe, but you can't burn it?  Try K3b.  It's a KDE program so you're likely to end up downloading quite a few dependencies as well.  I've used K3b for years with great success, including burning ISOs created by DeVeDe.

---

### Post by haqking on 2011-06-25
I missed a post further up

---

### Post by nifty542 on 2011-06-25
Hi, all

I am really confused. I did manage to burn a dvd, but it repeatedly plays a the menu and title. Circular insanity, again.
Obviously, I have done something wrong, but the help files for DeVeDe are rudimentary, to say the least.
Thank you, in advance, for your patience with my clumsiness.
Regards
Nifty

---

### Post by nifty542 on 2011-06-26
Hi, all

I installed WinFF and used it to convert to Pal DVD widescreen. All seemed to go ok, but I still get the same message in Brasero.
Any further suggestions would be greatly appreciated
Regards
Nifty

---

### Post by ron999 on 2011-06-26
> **nifty542 said:**
> 
Any further suggestions would be greatly appreciated

Now that you've created an MPEG-2 file, 'author' it to create the **audio_ts** and **video_ts** folders.

---

### Post by nifty542 on 2011-06-26
Hi, many thanks for the reply.
I am afraid I have no idea what that means.
I have installed DVDAuthor, but don't know how to use it.
Regards
Nifty

---

### Post by ron999 on 2011-06-26
> **nifty542 said:**
> 
I am afraid I have no idea what that means.

Hi
To author a simple DVD from a single MPEG-2 file **dvdauthor** can be used.
If you want a menu and multiple files then something more sophisticated is needed.

('**author**' means to create a [B]Directory and file structure
[/B] for a DVD disc. Read about it here:- [http://en.wikipedia.org/wiki/DVD-Video#Directory_and_file_structure]("http://en.wikipedia.org/wiki/DVD-Video#Directory_and_file_structure"))

---

### Post by nifty542 on 2011-06-26
Hi
Thanks for the reply.
As I said, I have no idea what that means and I don't know how to use DVDAuthor
Regards
Nifty

---

### Post by nifty542 on 2011-06-26
Hi
I have just read the page. I don't understand it. Back to Windows?
Regards
Nifty

---

### Post by nifty542 on 2011-06-26
Hi, all
I have enabled all the repositories I can. I tried to read the Wiki page on DVD, but it might as well have been written in a language I don't understand.
I have googled for this and, apparently, QDVDAuthor provides a gui for DVDauthor. But, I can't find it in the repos. I know it was there when I used to use Mepis.
So, I downloaded it, but don't understand the instructions for installation.
I first tried Linux in 2006, and I'm afraid I feel that I'm making very little progress.
In Windows, I use Serif Movieplus, and it is easy to create chapters and burn a DVD.
For ethical reasons, I would like to ditch Windows- but I am encountering so many problems, I am wondering if it is worth all the trouble.
If I get a reply, thank you
Regards
Nifty

---

### Post by uRock on 2011-06-26
I've been using DeVeDe for creating playback media.

---

### Post by nifty542 on 2011-06-26
Hi
Thanks for the reply. As mentioned earlier in this thread, I encountered a serious problem using DeVeDe. I still can't get it to work.
Is there anyone who can take me through a solution. step by step?
Anyone?

---

### Post by uRock on 2011-06-26
You have to convert the m4v files to mpg. TO do this, first install ffmpeg via Ubuntu Software Center, then to convert the video you will need to open a terminal, then use the cd command to get the terminal to the directory containing the video file, then use the following command to tell ffmpeg to convert the file (note: this process takes a while),```
ffmpeg -i NameOfVideo.m4v -target ntsc-dvd NameOfVideo.mpg

```

---

### Post by josephmills on 2011-06-26
first open your termianl and type in 

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


``` then 

```
sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update
```


then 

```
sudo apt-get update && sudo apt-get upgrade  
``` 
then 

just to make sure everything is installed try a 

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
``` 
then 
```
sudo apt-get install ubuntu-restricted-extras
```

then 
go to ubuntu software center then EDIT-->SOFTWARE SOURCES 

than make sure all are ticked [IMG]http://img841.imageshack.us/img841/9224/screenshot15kq.png[/IMG][IMG]http://img861.imageshack.us/img861/4778/screenshot16i.png[/IMG]


then 
close out of everthing and open a terminal again and type in 
```
sudo apt-get update && sudo apt-get upgrade 
``` 

then open up brasero and try to burn again. Anything? kif not we will play with the good bad and ugly packages


if any thing happens post the whole termianl output

---

### Post by uRock on 2011-06-26
> **josephmills said:**
> first open your termianl and type in 

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


``` then 

```
sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update
```


then 

```
sudo apt-get update && sudo apt-get upgrade  
``` 
then 

just to make sure everything is installed try a 

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
``` 
then 
```
sudo apt-get install ubuntu-restricted-extras
```

then 
go to ubuntu software center then EDIT-->SOFTWARE SOURCES 

than make sure all are ticked [http://img841.imageshack.us/img841/9224/screenshot15kq.png](http://img841.imageshack.us/img841/9224/screenshot15kq.png) [http://img861.imageshack.us/img861/4778/screenshot16i.png](http://img861.imageshack.us/img861/4778/screenshot16i.png)


then 
close out of everthing and open a terminal again and type in 
```
sudo apt-get update && sudo apt-get upgrade 
``` 

then open up brasero and try to burn again. Anything? kif not we will play with the good bad and ugly packages


if any thing happens post the whole termianl output

Not sure that is going to help the OP. Files from the net aren't going to be encrypted and if the OP is able to view the files already, then installing more codecs won't help with burning a DVD. I have all of the packages you mentioned installed and Brasero is still incapable of burning m4v to DVD.

---

### Post by josephmills on 2011-06-26
> **uRock said:**
> Not sure that is going to help the OP. Files from the net aren't going to be encrypted and if the OP is able to view the files already, then installing more codecs won't help with burning a DVD. I have all of the packages you mentioned installed and Brasero is still incapable of burning m4v to DVD.

just steps to make sure you know start from the start. I think that it has something to do with the good bad and ugly gstreamer. you are right about m4v it need to be converted but lets make sure that the codecs are there dont want to pull hair out trying to fix something that might just be super simple like you said  YOU have all the codec that I mentioned installed. sorry if I got in the way I have the utmost respect for you as I know that you are super smart

---

### Post by uRock on 2011-06-27
Nifty, Have you been able to convert files, then create the image with DeVeDe? I know it is truly time consuming, since m4v has to be converted, then DeVeDe converts them again as it creates the ISO.

---

### Post by nifty542 on 2011-06-28
Hi, all
Many thanks for the replies. I have been away on a job interview for two day (boring, I know, sorry).
I have been able to convert the files, that was fine. Then, I tried to burn using Brasero, and got the error message mentioned earlier. 
My problem is, I just don't know what to do with the files- there are 12 of them- to put them in the right order, and burn them to a playable DVD. 
By the way, I am hoping to use this in the classroom- it is "Stone Cold", originally aired by the BBC and unavailable as a DVD.
BUT, I am uneasy about continuing to use Windows, and would like to make a complete switch.
Many, many thanks for your help and advice
Regards
Nifty
PS. Got back late tonight, so apologise in advance if I haven't read your posts properly.

---

