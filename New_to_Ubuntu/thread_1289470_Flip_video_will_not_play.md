---
title: "Flip video will not play"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by freeediver on 2009-10-12
I have received flip video messages in the past but now I am unable to download a video message sent to me.
I get RSL error 1 of 1, and in the text block/strip below the viewing area I see an error message, Error 2046.It looked like the video was loading then it stopped and gave me the error messages,
I called Flip and they don't know what it is, does anyone have a clue why I can't download my video message after it has been uploaded to the Flip site then sent to me from the Flip message web site??

---

### Post by cariboo on 2009-10-12
Not knowing what a Flip video is, do you have all the proper codecs installed? Make sure you have the ubuntu-restricted-extras from the main repositories and the w32codecs or w64codecs from the Medibuntu repositories installed.

---

### Post by freeediver on 2009-10-12
Sorry it is a Flip Ultra.
I do not plug it into my computer so I did not think
it mattered what model it was. I am just trying to view
video clips sent to me through email.

---

### Post by freeediver on 2009-10-16
How do I check and what do I look for?

---

### Post by SPr on 2009-10-17
Which application gives the error 2046?

---

### Post by freeediver on 2009-10-17
no  special application. This happens when I open the hotmail message telling me I have a flip video.
I click the flip link and a page/window opens for the video share site.
The error code is seen below the flip video window in a text box on the flip video, video share page.

---

### Post by SPr on 2009-10-17
So, the error is on the website not your computer. Apart from notifying the owners there isn't much you can do.

When you told them about this error did you tell them it was problem with the site and had nothing to do with your PC?

---

### Post by freeediver on 2009-10-17
I am now going back and forth with them. They tell me they only support Windows and Mac also to check if I have the current version flash installed. I checked, I believe I have everything current.
The video attempts to DL gets about 1/2 then I get the error message.

---

### Post by SPr on 2009-10-17
Hmmm, if the site uses flash then that could be the problem (though it is still a partial problem with the site for not supporting Linux).

How did you install flash? Flash is in the Debian repos
> 
aptitude search flash
...
p   flashplayer-mozilla             - Macromedia Flash Player                   
i                - Adobe Flash Player - browser plugin       
p   flashplugin-nonfree-extrasound  - Adobe Flash Player platform support librar
...

I used 
```

aptitude install flashplugin-nonfree

```
Do you have another browser to try. Sometimes flash based sites don't work with the Opera browser but do with Epiphany or IceWeasel (Debian version of Firefox).

---

### Post by freeediver on 2009-10-17
Now to add a new twist I can play the video clips if I use my old,old windows machine.
I'm missing something in my install I just do not know what it is.
Thanks for any help and ideas.

---

### Post by freeediver on 2009-10-17
I tried copy/paste in terminal the line you gave and got this at the end.
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
laptop:~$

---

### Post by SPr on 2009-10-17
Try
```

sudo aptitude install flashplugin-nonfree

```

You'll need to be root to install anything from the repos.

Also try another browser.

---

### Post by freeediver on 2009-10-17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   

Thats what I got so I assume I already had everything
Its still not working tho

---

### Post by SPr on 2009-10-17
Have you tried another browser yet?

Search Synaptic if you only have one installed.

---

### Post by freeediver on 2009-10-17
Nope
Problem is that it did work thru my hotmail in the past. I do not want to change from Firefox just to view flip video.
O well
Time for me to get some sleep I will likely get called to work before the night is over.
Thanks for the help, I'll keep plugging away.

---

### Post by SPr on 2009-10-17
You can have many browsers as you can find installed. I have four or five I've installed and never bothered removing. Use one for the videos and your prefered browser at other times.

---

### Post by freeediver on 2009-10-18
Dumb and lost I guess.
How would a different browser affect my ability to play a video clip thru my hotmail?
Are you familiar with how flip video private video sharing works?
I get a message in my hotmail from the sender telling me a video is waiting.
I click the link and a new page opens.
I select the video clip to watch.
It starts to DL then stops 1/2 way.
A text box is directly below the small video window, in this box
a find my error message. #2046.
Flip video says they will not help me they will only support MS and Mac.

I am also a bit lost when I try to search for Flip video information. When I enter Flip Video in Search bx's the search seems to think I am trying to find a way to flip direction I guess. I can't be the only person here to receive flip video messages or am I the only one who is unable to receive them?
A few of the searches have given me threads with 100's of entries
and theat does not help much either.

---

### Post by imchipbrown on 2009-12-30
I have the same issue.  Ubuntu Hardy, Firefox 3.5 (and Chrome and Galleon).  Same exact description as above.  The Flip Video has a link to a Promo which plays just fine.  

Video system is Intel 915GM.  Totem 2.22.1.  Shockwave Flash 9.0 r246.  Tried to install Flash 10.  System says I already have the latest Flash?

---

### Post by imchipbrown on 2009-12-31
Solved for me.

I tried apt-get remove and purge stuff (unquoted here because it didn't work).  I went into the Symantic Package manager, searched for flash and found I had two instances.  Don't remember the details except one looked like adobe-flashplugin and another said something similar with the word restricted in there someplace.  I selected both (which were shown as being installed) and marked both for complete removal.

I then went to Google maps and tried a Street View.  It told me I needed Adobe Flash and with a click led me to Adobe's download site.  I downloaded/installed the .deb for Ubuntu 8.04.

I had done this a number of times previously, and the Package Manager said I already had the version installed (10.something) while everything else said I had 9.something, even after telling it to reinstall.

This time, my Shockwave Flash showed as Version 10.0 r42, StreetView worked again (as it had before I started really fooling around) and low and behold, the Flip Video no plays.

So, I think the Symantic complete removal of the two installed Flash helpers/libraries/whatever and then the fresh copy from Adobe's site is what fixed me up.

---

