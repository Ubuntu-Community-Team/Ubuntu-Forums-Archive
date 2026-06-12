---
title: "Brasero does not let me write to optical media"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by DaveKlynch615 on 2009-07-24
Hello everybody,

I tried performing a search to see if I could find someone else who has had the same issue but had no success.

Is there any reason why Brasero will not provide the option for me to burn the disc that is in the DVD writer drive?  When the burn dialog comes up, under the **"select disc to write to"** item, the **only** option provided to me is **"Image File."**  It does not provide an option to write to a DVD or CD.

Yet I believe Brasero is detecting the inserted disc: when the disc is inserted, it knows it is a single-layer 4.7gb disc because the data meter on the bottom right-hand side of the screen changes from 8.5gb to 4.7.

I am able to burn discs with K3b without any problem but I would prefer to use Brasero if possible since it is meant for Gnome.

I am using Ubuntu 8.10 with an HP Pavilion dv5000 laptop.  I believe my DVD writer is a TSSTcorp CD/DVDW TS-L532R.

Thanks,
Dave

---

### Post by LewRockwell on 2009-07-24
perhaps there are improvements which will satisfy your problems in 9.04

LiveCD to test system first before fresh install jaunty

.

---

### Post by wojox on 2009-07-24
It already knows you want to burn it thats why that screen came up. Didn't you try it?

---

### Post by DaveKlynch615 on 2009-07-24
> **wojox said:**
> It already knows you want to burn it thats why that screen came up. Didn't you try it?

The issue is that it is not letting me burn; I can only write an image file.


Here is a visual aide to help me describe the problem:

[IMG]http://farm3.static.flickr.com/2492/3754156658_7f402f31ca_o.png[/IMG]

Creating an 'Image File' is the only option provided to me in the drop-down menu under the part where it says 'Select the disc to write to'.  Therefore, when I click burn, it will only create an image file.

Maybe I'm missing something but if my system was working properly, I'd assume that that it would provide at least two options in the drop-down menu which would likely be:
->'Image File' (which is already there)
->burn to disc (which is not there)

---

### Post by pbotros1234 on 2009-07-24
First try:

```
gpasswd -a <YOUR USERNAME> optical
```


If that doesn't work, in a terminal type:

```
gksudo brasero
```


Those should work.

Just for insight, the first command adds your user to the "optical" group of users, meaning you will have permission to write to optical media.
The second command runs brasero as root, and that should usually take care of most permission problems.

---

### Post by DaveKlynch615 on 2009-07-25
I tried both commands: I couldn't get the first command to work, but I did get the second command to work.

It must not be a permissions issue as running Brasero as root didn't solve the issue.  

On another note, I can still burn with K3b.

I'm thinking that the version of Brasero that I have (0.8.2) has an issue with my particular optical drive.  

Any more suggestions are most certainly welcome and thanks to everyone who has given their input so far :)

---

### Post by DaveKlynch615 on 2009-08-04
> **LewRockwell said:**
> perhaps there are improvements which will satisfy your problems in 9.04

LiveCD to test system first before fresh install jaunty

.

Yes sir.  I appears that this issue has been patched in later versions of Brasero (or at least the version that comes with Jaunty).  I took my Jaunty live CD for a test drive and the version of Brasero on that detects my writer.

So if anyone else is having this problem, upgrade to Jaunty or install the latest Brasero.  I'm planning on upgrading to Karmic when that comes out so I'll just use K3b until then.

---

### Post by Arup on 2009-08-04
Also make sure to disable normalize in edit>plugins


This one gives lots of issues.

---

