---
title: "Lynksys Wireless &amp; ndiswrapper"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by hecter on 2008-03-04
Alright, let me start off with saying that I've taken a look at [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=574501") thread, and whenever I try to install I get  a hugely large slew of errors :( I've never used a linux OS before (I'm currently using Vista, so please help, I'm desperate!) and I've spent the past five years on a mac, which seems to have made me a wee bit computer inept. I don't have the Ubuntu CD anymore, and I have the ndiswrapper version found in the thread. It just doesn't seem to want to install... I put the code into the terminal, it goes through the first bit, and then I get a whole bunch of errors which I believe have a whole bunch of file names of the ndiswrapper folder... I got as far as extracting it. If you help me I'll love you forever!... And give you pie and cookies.

---

### Post by {BzF}~JOKesTER on 2008-03-04
assuming you have ndiswrapper installed:

In The Taskbar - Click: "Places" -Then- "Computer" -Then-"Filesystem" -Then- "Etc" -Then- "ndiswrapper" -----In "ndiswrapper" Delete All The Folders You See Even "Auto" -{Don't Worry This Doesn't Damage Your System In Anyway} -----Now That "ndiswrapper" Is Empty Do This:
 Goto Your CD For You Wireless Adapter - And Find The XP Driver Folder {This Varies From Manufacturer To Manufacturer} ----Right Click A File In This Directory And Goto - Properties.
 Copy And Paste The "Location" Of The File And Close The Dialogue Box -------Now - Open A Terminal And Type:

cd (Paste That Location Here)

#Than Type:

ndiswrapper -i (NameOfTheDriverInTheXPDriverDirctoryHere).inf

Now It Should Say : -Installing...

And Than Type:

ndiswrapper -l  

#It Should Show You What Drivers Are Installed Here If The Driver Says "Invalid" Than You've Installed It Wrong.


And

ndiswrapper -m

And

ndiswrapper -ma

And

ndiswrapper -mi

And That Should Be It!!! 

Now Plugin Your Wireless Card And Restart Your Computer!!

If The Light Blinks On The Wireless Card -{If There Is A Light} Than Your Good To Go!!

Otherwise You Might Be Using The Wrong Driver.

Connect To Your Network And Enjoy!!!

I Hope This Helps!

Note: {If Anyone Wants To Add To This Post Feel Free Too}
'

---

### Post by hecter on 2008-03-04
That's the thing, when I try to install ndiswrapper it just gives me a big long thing of errors :(

---

