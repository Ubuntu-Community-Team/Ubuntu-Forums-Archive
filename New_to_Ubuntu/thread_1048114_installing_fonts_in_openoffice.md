---
title: "installing fonts in openoffice"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by savat on 2009-01-23
I've been using Linux for three years now but still consider myself a beginner. I will apologize in advance for this question, because I know that the "answer" is supposedly online and in the OpenOffice help files but I have had no success with this. I am aware of RTFM. I have never posted on a Linux forum to find the answer to any question, I've always Googled the answer but this one stumps me and it's driving me CRAZY.

I can't install fonts into OpenOffice.

I use Intrepid Ibex.

Can someone PLEASE give me simple step-by-step instructions.

---

### Post by Kobalt on 2009-01-23
Here you go : [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by Kellemora on 2009-01-23
HI Savat

One doesn't INSTALL Fonts in Linux or directly into Open Office!

They are stored in a file named 
/usr/share/fonts/truetype for ttf fonts.
This is WHERE Open Office will look to find the fonts it shows as available as well.

One of the first things you will want to do is install
msttcorefonts from Synaptic, it will appear as it's own folder in
/usr/share/fonts/trutype/msttcorefonts.

You only have to cut n paste fonts into the fonts folder, you can nest folders if you like so each style of font is in a different folder, something you cannot do in the Doze.

Also, you can RENAME the individual fonts with any name you choose, I use the CORRECT NAME for the font to make it easier to find duplicates when they occur.  Which can cause some minor problems in Linux.
For example:  You may get a font named Darby that came with a printer install, but the file name is M76BR25A.ttf and you could get that SAME font with a new program you installed under the file name BDarby78.ttf and it's the SAME FONT.
This can cause both fonts to appear on the same page as blurred text since they may have registered differently.
My only point is, if you loaded some new fonts and then suddenly one or more don't work right, it's often because you have the same font twice.

You will find suggestions to place fonts in a hidden folder in your /home directory.  I Strongly suggest you do not put fonts ANYWHERE other than WHERE THEY BELONG.  If you have WINE installed, make sure that font folder remains EMPTY also!

TTUL
Gary

---

### Post by savat on 2009-02-03
Thank you both for your help...

---

### Post by halitech on 2009-02-03
> **Kellemora said:**
> HI Savat

You will find suggestions to place fonts in a hidden folder in your /home directory.  I Strongly suggest you do not put fonts ANYWHERE other than WHERE THEY BELONG.  If you have WINE installed, make sure that font folder remains EMPTY also!

TTUL
Gary

and why would you strongly suggest that fonts are only put in that folder and not in a hidden fonts folder in the users home directory? what happens if they had actually purchased a font, forgotten about it and installed a new distro while keeping the old home folder? Wouldn't it be easier for backup purposes to have the extra fonts in their home folder where they can be easily backed up?

not trying to start anything, just curious as to why you strongly suggested it.

---

### Post by Kellemora on 2009-02-04
Hi Hali

We maintain thousands upon thousands of fonts here, only a few are assigned to each computer, depending upon which ones we need for those clients being processed on those computers.

That's one of the FINER Points of Ubuntu (the ability to keep fonts in separate folders)!

If you maintain a separate fonts storage file for all fonts elsewhere, that is fine, just make a backup folder of the fonts you use most often and which ones are required by the system and keep those separate for quick reload if you ever do need to restore your system.

But the PRIMARY REASON to keep your fonts TOGETHER in one place is to avoid DUPLICATE FONTS being loaded onto your system.  Which can still happen anyhow because Fonts can be stored under ANY Filename one chooses........
Almost every times someone has a problem with scratchy looking fonts, scratched out fonts, blurred fonts, shadowed fonts, etc.  It was because they had two or more of the same font loaded on their computer, not knowing a font was stored somewhere else already, or under a different file name for the font itself.

So if you have fonts where they normally load, plus fonts in msttcorefonts AND fonts in a hidden folder in each users home directory.  You may NOT know Mary placed a font in her home folder and duplicated it where it belongs, then suddenly Mary is screaming her program is messed up, can't even read the title bar, etc.  It's just black streaks........  You then lose about 6 hours or more trying to find out what happened.

Thus it's better to store your fonts where they belong, rather than creating new hidden places to store them in.

Before I started using a Data File Server, I kept all fonts in a folder named MasterFontsFile in my home directory.  Programs didn't find them there!  And besides the Master File that held every font, there were separate client folders that held the fonts for that particular client IF they were not standard system or daily use font files.  Doing it this way has saved mucho headaches!  And since I do a lot of newsletters, I have a different font folder for each of those particular newsletters as well on the Data File Server, so no matter which computer I sit down at, I can pull (copy) that folder to the computer and go right to work.  When I'm done, dump the folder in the trash can so it's not available to clients not authorized for that font.  Most of our fonts are proprietary and owned by particular clients also.  Can't have those floating around!

We even keep the fonts folder in WINE completely empty too!

TTUL
Gary

---

### Post by halitech on 2009-02-05
I can see your point in a business setting (especially having client owned fonts) where you have a data file server but my personal opinion for a personal computer where there might be 1 or 2 users, its easier then telling them to put them in the /usr/share/fonts/truetype because they don't own that folder so you would then need to explain to them how to use gksu nautilus to get a root file manager and how to get to the folder, etc, etc. Plus they also then have the danger of either not putting them were they belong or possibly removing something (font or otherwise) that may cause problems. 

Just my opinion which doesn't make either of us right or wrong :)

---

### Post by Kellemora on 2009-02-05
Hi Hal

I'm not sure about this, but, wouldn't they still need root privileges to create a HIDDEN folder, even in their own userspace?????

And, correct me if I'm wrong here!  I thought programs that use fonts checked ALL USERS directories for various fonts it was looking for, regardless of which User opened the program.

I'm only saying the above from a problem I had months ago when I first started using Ubuntu.  I had placed client owned fonts in a hidden directory .fonts for the User who required access to that font.  I figured that way it would be safe from other users.
Then from my desk, when I went to select a font for myself, I saw them listed in OOoWriter and they were NOT installed on my file folder at all.  Only in that users folder, at my desk too, because she was getting ready to create the print masks for the printer.  I was not logged in under her username, only under my username.  

Nonetheless, this was a great learning experience for me, because prior to this incident, I did not know I could have fonts inside of nested folders.  Once I learned I could do that, it was yet one more GREAT reason to convert my office over to Ubuntu!  The DOZE would CHOKE if too many fonts ended up in it's fonts folder!

Ubuntu also gave me the courage to set up an independent Data File Server (just file sharing from a dedicated machine, not a server server).......I did mess with Edubuntu as a learning tool first, but that was not the way to go for my operation and the machines I have here.

I still suggest that a user keep all of their fonts in ONE LOCATION, so they know where they all are!  And to pick their favorite ones and store all the rest ELSEWHERE but viewable and accessible should the need arise to use one.
Ubuntu is great for that because it displays fonts stored in storage folders using the automatic font viewer if it's turned on.

Despite the few pitfalls, the more I use Ubuntu, the more Time Saving Features I run across that are built into it!  Or download-able through Synaptic.

TTUL
Gary

---

### Post by halitech on 2009-02-07
> **Kellemora said:**
> Hi Hal

I'm not sure about this, but, wouldn't they still need root privileges to create a HIDDEN folder, even in their own userspace?????

not that I've ever run into in my home folder

> And, correct me if I'm wrong here!  I thought programs that use fonts checked ALL USERS directories for various fonts it was looking for, regardless of which User opened the program.

I'm only saying the above from a problem I had months ago when I first started using Ubuntu.  I had placed client owned fonts in a hidden directory .fonts for the User who required access to that font.  I figured that way it would be safe from other users.
Then from my desk, when I went to select a font for myself, I saw them listed in OOoWriter and they were NOT installed on my file folder at all.  Only in that users folder, at my desk too, because she was getting ready to create the print masks for the printer.  I was not logged in under her username, only under my username.  

they possibly might show up in other peoples accountts if the directory is not setup in such a way to prevent other users from accessing the home partition but as I only have a single user machine (other then root) I've never noticed that

> Nonetheless, this was a great learning experience for me, because prior to this incident, I did not know I could have fonts inside of nested folders.  Once I learned I could do that, it was yet one more GREAT reason to convert my office over to Ubuntu!  The DOZE would CHOKE if too many fonts ended up in it's fonts folder!

thats the great thing about linux, it allows the freedom to do things in a logical manner that windows doesn't :)

> Ubuntu also gave me the courage to set up an independent Data File Server (just file sharing from a dedicated machine, not a server server).......I did mess with Edubuntu as a learning tool first, but that was not the way to go for my operation and the machines I have here.

I haven;t gone that route but I do run a few server apps from my main system for personal use

> I still suggest that a user keep all of their fonts in ONE LOCATION, so they know where they all are!  And to pick their favorite ones and store all the rest ELSEWHERE but viewable and accessible should the need arise to use one.
Ubuntu is great for that because it displays fonts stored in storage folders using the automatic font viewer if it's turned on.

I think in this we will have to agree to disagree but thats the great thing about linux, the freedom and the choice to do things the way each person sees fit. :)

> Despite the few pitfalls, the more I use Ubuntu, the more Time Saving Features I run across that are built into it!  Or download-able through Synaptic.

TTUL
Gary


I agree, I've been basically a linux only user for 3 years now and there are so many faster ways to do things that save time and make using a computer actually enjoyable again :)

---

### Post by benjoseph on 2009-02-09
Go to home-folder-view, and tick "Show Hidden Files". Create a directory ".fonts" then if you need fancy fonts go to: [http://www.webpagepublicity.com/free-fonts-a3.html#FreeFonts](http://www.webpagepublicity.com/free-fonts-a3.html#FreeFonts), and download as many fonts you like. Then copy those fonts in the ".fonts" directory you have previously created, and enjoy the result.

---

### Post by Bearly Able on 2009-03-11
I followed the instructions above and added a custom fonts folder to my home folder.  Then I used gksudo nautilus and copied it from there into /usr/share/fonts/truetype/ so that my husband can also access them.  Works a treat.  

I've just attempted to do the same on the laptop, but Open Office is not reading my custom fonts from either location.  I get an error message telling me I do not have permission to read my new folder in /usr/share/fonts/truetype/.  I'm sure I followed exactly the same procedure.  Both machines are running Ubuntu Hardy, but the PC has Open Office 2.4, while I've just installed Open Office 3 from the .deb on the laptop, to solve a different problem.

I'm guessing I need to change the permissions on the shared folder, but I'm not sure how to do that.  Can anybody help, please?

---

### Post by Bearly Able on 2009-03-19
OK, I've solved both problems.  The fonts folder in my home folder, I'd forgotten to preface with a . to make it hidden.

I found the answer to my other problem in [a completely different thread]("http://ubuntuforums.org/showthread.php?t=1100429").
> Running GUI apps with "sudo" instead of "gksudo" might break things to the point that you are not able to log in any more..

"sudo" doesn't load root user's environment variables for graphical apps like gksudo does, this means that you are running the app as root, but using your normal user's home directory and configuration files. In some cases this will result in your normal user's files becoming owned by root.

Of course some apps work fine with sudo, at least most of te time, but it sure is easier and simpler to just use "gksudo" with all GUI apps and "sudo" with CLI apps than try to find out which ones work fine and which ones will break things.. After so long, I can't honestly say that I used sudo instead of gksudo, but I might well have done, and redoing the process with gksudo works, so I guess that's where I went wrong.

Thanks, mcduck!

---

