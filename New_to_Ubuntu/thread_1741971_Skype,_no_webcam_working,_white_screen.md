---
title: "Skype, no webcam working, white screen"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by JosephL on 2011-04-28
I seriously dont know what to do, Ive googled and read a lot of pages in thsi site, im using ubuntu. maverick Meerkat, Gnome, I have installed the beta version of skype, because the webcam wont work with aMsn or Empathy.
I really don't know what hapened, the webcam was working just fine with skype and suddenyl out of nowhere next tiem I wnated to video chat, I couldnt, I got the other person's image, but mine was all white, or black, they do get the audio from the built-in mic of the webcam, the webcam im using is the Genius Slim 2020AF.
I really know little about creating codes, nothing about scripts.
my dad has installed time keeper, if time keepr logs me out while I was using skype or amsn or any other application, can this have any effect on those applications? like it makes then no work anymore in certain areas or something.. I don't know.. LIke I said, I know nothing about this, just a little, ive been using Linux for a short time, maybe some months,
any help would be appriciated, ive trie a lot of things posted in this webpage and others, and I dont kow what to do... nothing is working...

---

### Post by cariboo on 2011-04-28
How does the web cam work when you run cheese?

---

### Post by JosephL on 2011-04-30
> **cariboo907 said:**
> How does the web cam work when you run cheese?
doesnt work, its all black, by the way the computer is 32 bits

---

### Post by drpas2k on 2011-04-30
I followed this advice and webcam is working in Skype.

Re: HOW TO - make virtually any webcam work with Skype in Li

Postby grndplane on Tue Sep 28, 2010 12:36 am
" By Doruletz


(1) Install Skype v2.1.081 Beta either via Terminal (sudo apt-get install skype) or via Software Manager
(2) Install Video4Linux Control Panel (v4l2ucp) either via Terminal (sudo apt-get install v4l2ucp) or via Software Manager
(3) Run "v4l2ucp" from a Terminal (sudo v4l2ucp)
(4) From the top bar, select 'preview'.
(5) Select 'configure preview'.
(6) In the 'application to use line' replace mplayer with Skype.
(7) Click 'OK" and close the sub-menu.
(8) In the preview menu, select "start preview"
(9) This will start your Skype program. Sign in with your Username and Password and you are ready to go with Video Calls (just to make sure everything works, test your video - from Skype menu go to Options and Video Devices)"

Add step 10 to this list
(10) Create Skype Icon and in the command box put "env LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype" without the quotes.

This worked for me on both a netbook and a desktop.

---

### Post by JosephL on 2011-04-30
> **drpas2k said:**
> I followed this advice and webcam is working in Skype.

Re: HOW TO - make virtually any webcam work with Skype in Li

Postby grndplane on Tue Sep 28, 2010 12:36 am
" By Doruletz


(1) Install Skype v2.1.081 Beta either via Terminal (sudo apt-get install skype) or via Software Manager
(2) Install Video4Linux Control Panel (v4l2ucp) either via Terminal (sudo apt-get install v4l2ucp) or via Software Manager
(3) Run "v4l2ucp" from a Terminal (sudo v4l2ucp)
(4) From the top bar, select 'preview'.
(5) Select 'configure preview'.
(6) In the 'application to use line' replace mplayer with Skype.
(7) Click 'OK" and close the sub-menu.
(8) In the preview menu, select "start preview"
(9) This will start your Skype program. Sign in with your Username and Password and you are ready to go with Video Calls (just to make sure everything works, test your video - from Skype menu go to Options and Video Devices)"

Add step 10 to this list
(10) Create Skype Icon and in the command box put "env LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype" without the quotes.

This worked for me on both a netbook and a desktop.

thanks im gonna try that, we just updated ubuntu, to the 11 version, and I don't know how, the webcam is working in skype, I havent really made videocalls but in the test thing it works, that method you just posted is new for me havent heard of it before so im gonan try it, many thanks,

---

### Post by JosephL on 2011-05-03
> **drpas2k said:**
> I followed this advice and webcam is working in Skype.

Re: HOW TO - make virtually any webcam work with Skype in Li

Postby grndplane on Tue Sep 28, 2010 12:36 am
" By Doruletz


(1) Install Skype v2.1.081 Beta either via Terminal (sudo apt-get install skype) or via Software Manager
(2) Install Video4Linux Control Panel (v4l2ucp) either via Terminal (sudo apt-get install v4l2ucp) or via Software Manager
(3) Run "v4l2ucp" from a Terminal (sudo v4l2ucp)
(4) From the top bar, select 'preview'.
(5) Select 'configure preview'.
(6) In the 'application to use line' replace mplayer with Skype.
(7) Click 'OK" and close the sub-menu.
(8) In the preview menu, select "start preview"
(9) This will start your Skype program. Sign in with your Username and Password and you are ready to go with Video Calls (just to make sure everything works, test your video - from Skype menu go to Options and Video Devices)"

Add step 10 to this list
(10) Create Skype Icon and in the command box put "env LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype" without the quotes.

This worked for me on both a netbook and a desktop.

tested the video in the skype menu and i got black screen :/ then i tried to video chat by doing the 10th step and it wouldnt work either :/ if this helps, I once was using the terminal while using skype and at some points it said, that the webcam was recieving the image but it wouldnt show it, why? hope that helps :/ could all this be affected by other apps? what if i was using the webcam when time kepper kicked me out? would it make some permanent damage to the webcam codes or something idk.... also what about cairodock? or amsn? sorry im askig a lot :7 im really desperated and dont have much time cz im leaving somewhere in 9 days

---

