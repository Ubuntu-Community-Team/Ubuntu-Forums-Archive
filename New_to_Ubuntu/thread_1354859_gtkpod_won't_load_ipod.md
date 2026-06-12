---
title: "gtkpod won't load ipod"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by morisila.ardiel on 2009-12-14
Hi there fellow Ubuntu users! I've got a bit of a conumdrum for you:

I have been using gtkpod for several months with no problems, using it to connect my 5th gen ipod to my laptop. Recently however, gtkpod has not been loading my ipod, although my computer recognizes it as being plugged in. This has happened since I've updated to  Karmic Koala. I was wondering if it was a bug yet to be fixed, or if I am missing the solution to the problem somewhere? I have taken the time to un- and re-install the program, but to no success.
The menu for loading an ipod won't even come up with I click the option, and I'd really like to get some of this music back on my ipod so I hope that there is a solution to this. Many thanks!

---

### Post by zkriesse on 2009-12-14
It's not you....I had that issue...it's because there is currently not support for the new iPod. Up to the 4'th gen there is but not to the 5'th gen one...sorry.

---

### Post by LowSky on 2009-12-14
5th Gen video IPods (ie Classic models) are supported by other programs. I know for a fact that banshee works. Anything beyond the 5th Gen is going to be tough, like iPod nano, iPhones, iTouch, and such.

---

### Post by morisila.ardiel on 2009-12-14
Banshee didn't work either. I've installed Hipo as well. None of them work.

---

### Post by grandpa2390 on 2009-12-15
I am using a 4th generation 60 gb Ipod Photo and it won't work with gtkpod either. It has been working for months and then last night out of nowhere  when I decided to try making a playlist it stopped working. not only will it not load in gtkpod, it won't load in itunes, music won't even show up on the ipod. But when i plug it into Windows pc, and go into that hidden folder it is all there. when i plug it into ubuntu and go to that hidden folder it is all missing.

---

### Post by ElroyJetson on 2009-12-19
Same here. 4th Gen ipod which mounted under 9.04 would not mount under 9.10. 

A 3rd gen ipod mounted under 9.10 but kept spewing errors about lyrics in unending dialog boxes.

:confused:

---

### Post by computernerd1101 on 2009-12-22
I don't know how useful this is, but the Linux filesystem is case-sensitive. I was having trouble making gtkpod load my ipod until I thought of configuring it to load the media mount point /media/IPOD instead of /media/ipod. That solved my problem. I hope it's helpful to yours.

---

### Post by crazzy on 2009-12-22
[COLOR=#000000][FONT=Times New Roman][LEFT][FONT=Bitstream Vera Sans][FONT=Bitstream Vera Sans]This morning I got a shiny new iPod Nano. Good stuff. I've read that amarok supports the iPod so I thought this would present no problems. However, I've plugged it in via the USB port and am not getting any recognition from Mepis at all, let alone amarok - won't mount either automatically or manually. I've been into synaptic and downloaded anything that looks relevant - but still to no avail.[/FONT]
[FONT=Bitstream Vera Sans]I suspect this might have something to do with fstab or mtab (based on searching the forum). But beyond really basic copy and paste in konsole I've not really got much idea what I'm doing. Does anybody know what I need to to do to get mepis to recognise my new toy?[/FONT]
[FONT=Bitstream Vera Sans]
[/FONT]
[FONT=Bitstream Vera Sans]
[/FONT]
[FONT=Bitstream Vera Sans]
[/FONT]
[FONT=Bitstream Vera Sans]
[/FONT]
[FONT=Bitstream Vera Sans]
[/FONT]
[FONT=Bitstream Vera Sans]
[/FONT]
[FONT=Bitstream Vera Sans]
[/FONT]
[FONT=Bitstream Vera Sans]
[/FONT]
[FONT=Bitstream Vera Sans]_________________________________________________________________[/FONT]

[/FONT][/LEFT]
[/FONT][/COLOR]     [granite   countertops]("http://www.kitchendirects.com/countertops/granite-countertops.html")       [kitchen   islands]("http://www.kitchendirects.com/kitchen-fixtures/kitchen-islands.html")       [dish   rack]("http://www.kitchendirects.com/kitchen-fixtures/dish-racks.html")

---

### Post by morisila.ardiel on 2009-12-24
Rhythmbox seems to be working now, but I don't have nearly as much access as before. I'm just happy I can put music on the thing at all.

---

### Post by Abras on 2009-12-26
hmmm, I too have recently had problems with Gtkpod. After several weeks of success with my third-gen, 8 gig nano, yesterday I tried to load my iPod with Gtkpod, but to no avail.

The iPod seems to have mounted fine, and I can open and view my songs with Rhythmbox (though using it to add songs to the iPod doesn't seem to be working.)

So I'm left wondering... what's goin' on here?

---

### Post by falconindy on 2009-12-26
5th gen iPod working fine here with gtkpod. Without HAL and gvfs, too.

---

### Post by Kryptor on 2009-12-26
I was having the same problem after my update from heron to koala, but the fix for me was simple. In that I had forgotten to change the repository settings after I reloaded everything. From the edit menu go to repository/ipod settings then just fill out the info for your ipod. Oh and don't forget to save, I did. 
hope it helps!

---

### Post by Abras on 2009-12-27
That seems to have worked, Kryptor. Thank you. Now here's hoping everyone else here manages to fix their own problems (technical or otherwise :P :))

---

### Post by giovannif on 2009-12-27
> **Kryptor said:**
> I was having the same problem after my update from heron to koala, but the fix for me was simple. In that I had forgotten to change the repository settings after I reloaded everything. From the edit menu go to repository/ipod settings then just fill out the info for your ipod. Oh and don't forget to save, I did. 
hope it helps!

After the update to Karmic Koala I have a similar problem with my Ipod. Gtkpod does not load anything. I followed your thread and I came across with the above mentioned post. Could you please explain step by step what you did, because I haven't quite understood the meaning of the post.

Ciao
Gio

---

### Post by giovannif on 2009-12-27
I found the menu that Kryptor suggested. I am now able to recognize the iPod. I have also managed toi upload files. However when I disconnect the iPod I can't find anythyng. it seems that I messed the database list or something like that. In fact when I re-connect it with gtkpod I can see every file.
What is the proper configuration of the repo in gtkpod?

Thanks
Gio

---

### Post by newbette on 2009-12-28
Thanks Kryptor! Solved my problem.  

I have a new 160GB ipod classic and it only was able to load once until I read this post and checked the Edit menu and changed the settings.  My mount point had changed so I had to change it back to 

/media/ipod(or whatever your ipod is called)

as well as selecting the model of ipod.

---

### Post by Kryptor on 2009-12-29
giovannif did you click the "Save Changes" button that is next to "Load Ipod" on the main screen after loading your songs onto the Ipod? The way the gtkpod Repository Options menu is set up you probably have the settings right if you can recognize it since nothing will work unless you pick the correct mount point.

---

### Post by giovannif on 2009-12-29
> **Kryptor said:**
> giovannif did you click the "Save Changes" button that is next to "Load Ipod" on the main screen after loading your songs onto the Ipod? The way the gtkpod Repository Options menu is set up you probably have the settings right if you can recognize it since nothing will work unless you pick the correct mount point.

Yes I did. The funny thing is that I can see everything on the pc but when I disconnect the iPod, it seems there is nothing on the iPod.

I could fix this problem with the computer of my girlfriend which uses ubuntu 9.04. I connected the iPod and then used gtkpod with the same repository and preference configurations. Then I pressed "save changes" and disconnected. I could then magically see everything on the iPod, even the songs/videos that I loaded with Ubuntu 9.10.

I tried another thing: I used the program rythmbox to load just one song onto the iPod, and it happened exactly the same. When I disconnected it I was not able to see any song and I had to fix the problem using ubuntu 9.04.

Thank you for your help

Gio

---

### Post by giovannif on 2009-12-30
Just for the sake of your curiosity I found this "bug report" 

[https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/461639](https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/461639)

that describes the same problem I have, even though I use a classic iPod (Gb 160, B145) instead.

There should be an issue with how Rhythmbox, gtkpod and other similar program in Karmic are writing the database. Further investigation on it suggests that the problem is in libgpod4 0.7.2-1ubuntu1.

However the report suggest a solution for the iPod Nano only and I am still to find a way to make my iPod work.

Gio

---

### Post by LuisGMarine on 2009-12-30
Hello, for those of you guys still having trouble try this quick workaround and see if it works.  I ran into this problem with my 5.5 gen ipod in 9.10.  Pretty much rhythmbox was the only thing it could recognize it.

First of all unplug your ipod from your PC.

Then run this command in terminal, and plug in your ipod shortly after:

```
killall -9 nautilus
```

After you run the command and plug in your ipod, wait about 30 second (*important*) to wait. Then open up the run box by hitting Alt + F2 then type in "nautilus" with out quotations.  

Then open up what ever program you want to manage your ipod with and *hopfully* it should recognize it.  If it works, please keep in mind that you will have to do this every time you connect your ipod.  I hope this helps most if not all of you still experiencing ipod troubles in karmic koala.  :guitar:

---

### Post by morisila.ardiel on 2009-12-31
My gtkpod is working wonderfully now that I've made it through a couple of hoops to boot it on the gtkpod. I did forget to reset it when I reinstalled.

---

### Post by man_of_Tao on 2010-01-04
[LIST]
[*][FONT=Century Gothic][SIZE=3]computernerd1101's suggestion worked for me.[/SIZE][/FONT]
[/LIST]
[FONT=Century Gothic][SIZE=3]In gtkpod, go Edit, Repository/ipod options, in ipod mountpoint manually type media/Your-iPod or whatever your ipod's name is, exactly case-sensitive as it is. For example: media/BoomBox if BoomBox is the name of your ipod. Ok-it[/SIZE][/FONT][SIZE=3], and it should appear in the left pane. Good luck. [/SIZE]

---

### Post by Damodar on 2010-01-09
The suggestions on updating the repository worked for me as well.  Thank you all very much.  Here is what I did:  1) Open gtkpod iPOD Manager 2) Click Edit > Repository/iPod Options 3) Click the button "add new repository/iPod" 4) Set  Repository type: iPod Repository name: IPOD iPod mountpoint: /media/IPOD ITunesDB backup: (left it as what it defaulted) Model: (see note for how to find) Then click Add button and then Ok button. 5) Click Music > Save Changes.  Note: To find out the iPod model you can go to [www.apple.com](www.apple.com) and type in your iPod serial number which can be found on the back (or also on mine by going into settings > about) or you can use a site such as this one [http://www.wikihow.com/Check--Your--iPod%27s-Generation](http://www.wikihow.com/Check--Your--iPod%27s-Generation)

---

### Post by angheloko on 2010-01-12
Was experiencing the same problem a while ago. Here's an alternative solution I found [here]("https://bugs.launchpad.net/gtkpod/+bug/446035"):

> 
If you plug in your ipod you see the ipod on your desktop. So just right click on your ipod and select unmount. Don't select eject!. Then go to Places and your iPod should be in the list - just click on it to remount it. That's it.


---

### Post by instinct46 on 2010-05-17
I know this is an old post but the above examples did not help me on the new ubuntu 10, any how instead of boring you with fail after fail, this works straight out of the box Floola

[http://www.floola.com](http://www.floola.com)

Download it, Extract it, Run it, no configurations to do except choose your ipod model ^^

---

