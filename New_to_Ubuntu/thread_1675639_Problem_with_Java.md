---
title: "Problem with Java"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by DeviantGuy on 2011-01-25
I'm currently having a problem with Java. Does anyone here know the website Pogo.com? its a website owned by EA that hosts casual games (Puzzles, card games, etc.). Most of the games on the site run in a individual window. However when I start a game, The window comes up. It sits there for a few minutes and closes. Ideas?

---

### Post by sammiev on 2011-01-25
Try [this]("http://ubuntuforums.org/showthread.php?t=1634220&highlight=java") but remember to tab over to Yes and press enter when Sun Java ask you to ack there licence. GL :)

---

### Post by flyfishingphil on 2011-03-03
> **sammiev said:**
> Try [this]("http://ubuntuforums.org/showthread.php?t=1634220&highlight=java") but remember to tab over to Yes and press enter when Sun Java ask you to ack there licence. GL :)
Followed everything I could find (even a couple of other posting I didn't find before) and still can't get it operational. Get the side panel with the chat and players listings but the game itself doesn't show and it jumps to the "oops" page saying I need to install the Java.

Any other ideas?

---

### Post by Miljet on 2011-03-03
We are running Lucid and we use Pogo.com every day. It does require the Sun version of java. I can't remember if I got it from "lucid partner" or from "medibuntu".

Open system -> administration -> software sources. Click on the "other software" tab and make sure that the partner entry is checked. Close the software sources window.

Click on Applications -> Accessories -> Terminal. Then type in ```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

When you get to the EULA, you will have to press your tab key to accept it.

Last thing is to open System -> administration -> synaptic package manager. Search for and uninstall "Icedtea java. 

You should be good to go.

---

### Post by flyfishingphil on 2011-03-03
It was working fine until I did the updates recommended yesterday. Total confusion since then.

Tried that and it says it's already installed. Go to Pogo and now it pops up with the Sun Java download sign saying I don't have Java. Have tried several suggestions but still getting nowhere.

Did a full delete of Java. Went to Synaptics and marked all of the Sun Java for install. Went thru that sequence. Then checked Tools, Addons, in FF, and no Java is showing when I click on "check for updates".

Tried the default setting directions at ([http://sites.google.com/site/easylinuxtipsproject/java#TOC-Inform-the-system-and-make-the-new-]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Inform-the-system-and-make-the-new-") and can't get that to work either.

Is there anyplace that has directions on this that starts with "Step 1: Turn computer on"?

Just think, a week ago I couldn't spell "computer illiterate" now I am one!


Went back in and tried the Terminal directions.(sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts) It went thru the whole sequence this time. Will do a full shutdown and restart and see if it works now. Will be back and let you know.

---

### Post by flyfishingphil on 2011-03-03
OOOOKKKKKK!!!!! Now I'm really confused. Works on some but not on others. Can get in to Solitaire but not Addiction or Jigsaw games. Is there something else I need to do that style of action or is it just a conflict with something in Pogo?

Did some more checking and found lots of games I can't open and a few I can. Yes, Freecell and First class solitaire but no on any of the slots, Pogo Addiction, Jigsaw Treasure or Detective and several others I tried.

Guess if push comes I can always go into VBox and do Pogo thru XP. (Hate that idea!)

---

### Post by iheartubuntu on 2011-03-03
Miljet has the correct answer. Follow those instructions.

Pogo.com needs Sun Java to work so you will need to install Sun Java and remove the iced tea version of java. And then it only works in Firefox. It does work though!

As a side note, whenever there is an update to icedtea, ive found that it removes my sunjava. In the past ive had to go into synaptic and lock the current version of sunjava so it doesnt get removed.

---

### Post by NCLI on 2011-03-03
> **iheartubuntu said:**
> Miljet has the correct answer. Follow those instructions.

Pogo.com needs Sun Java to work so you will need to install Sun Java and remove the iced tea version of java. And then it only works in Firefox. It does work though!

As a side note, whenever there is an update to icedtea, ive found that it removes my sunjava. In the past ive had to go into synaptic and lock the current version of sunjava so it doesnt get removed.

This happens because part of Icedtea is still on your system. Make sure to remove all of it.

---

### Post by Penny N. Nickels on 2011-03-03
I'm with the others with trouble with the Java on Pogo.com & their outlet on Facebook (Pogo Games). 

The following is their suggestion (from their news page): 
>  
[ Bug With Newest Firefox Update Causes Issues in Some Games ]("https://bugzilla.mozilla.org/show_bug.cgi?id=629030")
  Recently Firefox released a new update to their browser (Firefox version  3.6.14). Unfortunately, this release introduced a bug that causes  issues with Java, and players who have upgraded will find that they're  unable to play Java games on Pogo. You can download the [Previous Version of Firefox]("http://download.mozilla.org/?product=firefox-3.6.13")  and use that - but be sure to go to Tools > Options > Update tab.  Make sure the "Ask me what I want to do" button is ticked rather than  the "Automatically download and install the update" button. 

There are no issues with [Internet Explorer]("http://www.microsoft.com/windows/internet-explorer/default.aspx") and [Google Chrome.]("http://www.google.com/chrome")   	 	 

I've tried just about everything suggested (here & elsewhere) to remedy this. While they claim there's no issues with IE or Chrome, I still cannot play games with Chrome. 

If I was to follow their suggestion of trying to revert to the previous version of Firefox, how would I do that? (I'm still a newbie!) Or, is there yet another way of handling it? HELP!

Thanks in advance.

PS - > This happens because part of Icedtea is still on your system. Make sure to remove all of it. Is that all Icedtea occurences in synaptic or just Icedtea java?

---

### Post by frenziedfemale on 2011-03-04
here is how I fixed this problem. Open Firefox, click on Help tab ... Troubleshooting Information ...
 the first line at the top of the page has a link to support website, click that. This will take you where you need to go. On the support page is a link to click for issues with Pogo.com. You can download the previous version of Firefox for linux right from there. (save the file, don't open the file from website). Quit firefox after download.

Now you need to install. I put the downloaded tar.bz2 file into my home/username directory for easy use. (this way you don't have to change directories to unpack the file.)

in terminal window type the following :
[SIZE=3][B][FONT=Arial Black]
[/FONT][/B][/SIZE][FONT=Arial Black][SIZE=3]tar xjf firefox-3.6.13.tar.bz2[/SIZE][/FONT][B][FONT=Arial Black]

[/FONT][/B][FONT=Arial Black][FONT=Arial]next type:
[SIZE=3]
[/SIZE] [FONT=Arial Black][SIZE=3]~/firefox/firefox[/SIZE][/FONT]
[/FONT][/FONT]
[FONT=Arial]Firefox should open with that command. Click the Help tab and then About to ensure that you are now running version 3.6.13. Close Firefox. Reopen using your icon/launcher, when Firefox  opens it should ask you if you want to disable the Add-on Firefox (en) 3.6, click disable ... or else you will just update back to the newest version.[/FONT]

 Hope this helps!

---

### Post by flyfishingphil on 2011-03-04
I said to heck with it and tried Google Chrome. Lots of problems there with lots of 'net sites so I tried Epiphany, copied and reloaded some info from FF links/bookmarks to the fresh Yahoo on Epiphany and am now using that. A little confusion when I first get to Pogo but it corrects itself and works well.

Not sure but it actually seems to be working a little faster than FF has been working. This keeps up I may drop FF completely and see if that causes any problems. 

Took a few hours to transfer all of info but seems to work just fine. Got the Epiphany browser in Ubuntu Software under applications.

---

### Post by Penny N. Nickels on 2011-03-04
> **frenziedfemale said:**
> here is how I fixed this problem. Open Firefox, click on Help tab ... Troubleshooting Information ...
 the first line at the top of the page has a link to support website, click that. This will take you where you need to go. On the support page is a link to click for issues with Pogo.com. You can download the previous version of Firefox for linux right from there. (save the file, don't open the file from website). Quit firefox after download.

Now you need to install. I put the downloaded tar.bz2 file into my home/username directory for easy use. (this way you don't have to change directories to unpack the file.)

in terminal window type the following :
[SIZE=3][B][FONT=Arial Black]
[/FONT][/B][/SIZE][FONT=Arial Black][SIZE=3]tar xjf firefox-3.6.13.tar.bz2[/SIZE][/FONT][B][FONT=Arial Black]

[/FONT][/B][FONT=Arial Black][FONT=Arial]next type:
[SIZE=3]
[/SIZE] [FONT=Arial Black][SIZE=3]~/firefox/firefox[/SIZE][/FONT]
[/FONT][/FONT]
[FONT=Arial]Firefox should open with that command. Click the Help tab and then About to ensure that you are now running version 3.6.13. Close Firefox. Reopen using your icon/launcher, when Firefox  opens it should ask you if you want to disable the Add-on Firefox (en) 3.6, click disable ... or else you will just update back to the newest version.[/FONT]

 Hope this helps!

I'll try that! Thanks!

---

### Post by flyfishingphil on 2011-03-07
OK, update to FF 3.6.15 is available and corrects the problem.

If you have not received the update yet, and are still having problems with places like Pogo, here are the steps I used to do the update. (Simple is good!)

Click on System > Adminstration > Update Manager
When the update manager opens click on "Check Updates". This brought up the update to 3.6.15. Clicked "Install updates". When it finished checked on Pogo and it seems to work fine.

Hope this helps.

---

