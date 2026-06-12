---
title: "A Non-Installing Package"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-12-13
A while ago I tried to install ttf-mathematica4.1 via Synaptic Package Manager on Ubuntu 8.10. Unfortunately, it failed to install for some reason.

Whenever I now use Synaptic to get other packages or update my system, it recalls that it hasn't finished the install of ttf-mathematica4.1 so tries to do it again, and of course it fails again. I've tried marking it for Reinstallation, Removal and Complete Removal, but every time I get the message such as those in the screenshots below.

I would prefer to have the package installed on my system, but if that's not possible I'd prefer to find how I can completely get rid of it to avoid constantly getting error messages when I use Synaptic. Does anyone have any ideas as to what I should do?

[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-ttf-mathcompleteremoval.png[/IMG]

[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-ttf-mathreinstall.png[/IMG]

---

### Post by Michael.Godawski on 2008-12-13
Have you tried the usual rescue lines like
```

sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by Roger Allott on 2008-12-13
> **Michael.Godawski said:**
> Have you tried the usual rescue lines like
```

sudo dpkg --configure -a
sudo apt-get install -f
```

Er ..... no. I'm a Linux noob!

What do those commands do? Shouldn't the package title (ttf-mathematica4.1) be in the arguments somewhere? And isn't apt-get just the same as Synaptic but through the command line interface instead of GUI?

---

### Post by Michael.Godawski on 2008-12-13
sry... good that you ask.

These commands should resolve any conflicts in the package repositories which might come up because of terminated installation or not properly ended ones.

Just fire them up and post any error messages which might get displayed. 
Perhaps there will be none :p.

---

### Post by Roger Allott on 2008-12-13
Nothing happened on the dpkg instruction. Just returned me to the prompt after I'd entered my root password.

The following was output after the apt-get instruction:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mathematica4.1 (4) ...
--2008-12-13 11:18:26--  http://support.wolfram.com/mathematica/systems/windows/general/files/MathFonts_TrueType_41.exe
Resolving support.wolfram.com... 140.177.205.40
Connecting to support.wolfram.com|140.177.205.40|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://support.wolfram.com/ [following]
--2008-12-13 11:18:28--  http://support.wolfram.com/
Reusing existing connection to support.wolfram.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `./index.html'

    [  <=>                                  ] 21,015      55.5K/s   in 0.4s    

2008-12-13 11:18:29 (55.5 KB/s) - `./index.html' saved [21015]

checking MathFonts_TrueType_41.exe
Downloaded file looks corrupted!
dpkg: error processing ttf-mathematica4.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mathematica4.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

That looks like what I've been seeing in the details area of Synaptic recently.

---

### Post by Roger Allott on 2008-12-13
The part of the output that I keep looking at is:

```
checking MathFonts_TrueType_41.exe
Downloaded file looks corrupted!
```

So, if that file is corrupted, how do I remove it? Where would it be? Is it just a case of finding it and deleting it, or would that cause some knock-on problems with it being half configured?

---

### Post by bapoumba on 2008-12-13
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505847](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505847)
There was a bug in the package. The bug looks fixed upstream, so it should come to the ubuntu repos.

---

### Post by Roger Allott on 2008-12-13
> **bapoumba said:**
> [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505847](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505847)
There was a bug in the package. The bug looks fixed upstream, so it should come to the ubuntu repos.

AHA!! That's helpful. Thanks.

If any others have a similar problem with this package, this is what I did to remove it from my package list (although I think some residual files remain on my HD):

```
sudo rm -fv /var/lib/dpkg/info/ttf-mathematica*
sudo dpkg --purge --force-all ttf-mathematica4.1
sudo apt-get remove -f
```

(originally proposed by David D Short)

---

### Post by simptechmike on 2009-01-07
> **Roger Allott said:**
> AHA!! That's helpful. Thanks.

If any others have a similar problem with this package, this is what I did to remove it from my package list (although I think some residual files remain on my HD):

```
sudo rm -fv /var/lib/dpkg/info/ttf-mathematica*
sudo dpkg --purge --force-all ttf-mathematica4.1
sudo apt-get remove -f
```

(originally proposed by David D Short)

Thanks. This was helpful for me to remove this annoying item.

---

### Post by b_umlaut_n on 2009-02-01
I just had this same problem, and a solution if you want to actually get the fonts (instead of just remove the package) is to edit the file [FONT="monospace"]/var/lib/dpkg/info/ttf-mathematica4.1.postinst[/FONT], which has the wrong URL to download the fonts from.

Or, you can do this (cut n' paste into a terminal):
```
sudo sed '65cURL="http://support.wolfram.com/technotes/fonts/windows/files/"' -i /var/lib/dpkg/info/ttf-mathematica4.1.postinst
sudo aptitude install ttf-mathematica4.1
```

---

### Post by aravindprasad on 2009-03-14
For those of you who want to add the package (or remove it), here is a simple solution in  steps

Step 1) Open the terminal window and type
[COLOR="DarkOrange"]sudo su[/COLOR]
enter your password and login as root. (Or if you prefer, you can sudo every command I am listing below.)
Step 2) [COLOR="DarkOrange"]apt-get install ttf-mathematica4.1[/COLOR]
Yes! I know. It will fail. This is just to make sure you have the files we need below. So if you made a recent attempt (in the current session), you may skip this step. If you dont know what I am talking about, just do it.
Step 3) [COLOR="DarkOrange"]gedit /var/lib/dpkg/info/ttf-mathematica4.1.postinst[/COLOR]
/var/lib/dpkg/info is where dpkg does all its caching (or whatever) of its installation files. Use vim (anything else) if you prefer to stay on the command line like me.
Step 4) In this file look for the below lines. You might have to scroll considerably
[COLOR="DarkOrange"]URL="http://support.wolfram.com/mathematica/systems/windows/general/files/"
FILE="MathFonts_TrueType_41.exe"[/COLOR]
Step 5) Change the URL lines from
[COLOR="DarkOrange"]URL="http://support.wolfram.com/mathematica/systems/windows/general/files/"[/COLOR]
to
[COLOR="DarkOrange"]URL="http://support.wolfram.com/technotes/fonts/windows/files/"[/COLOR]
Step 6) Save the file and exit the editor
Step 7) [COLOR="DarkOrange"]apt-get install ttf-mathematica4.1[/COLOR]
Now the install should work fine. Similarly you can remove it too using
[COLOR="DarkOrange"]apt-get purge ttf-mathematica4.1[/COLOR]


[COLOR="Red"]**Explanation:**[/COLOR] The URL for the file, MathFonts_TrueType_41.exe, mentioned in the config file is outdated. To tell the truth Wolfram decided to throw it into the archives because they came up with some newer version. So all that was there to do is to update the URL. 

To the dude(tte) who maintains this package: Just update the URL with the new URL I gave above to fix it and your package is rocking again.

Hope this helps. If you are finding any of the instructions above hard to follow, feel free to ask me for a clarification.

-AP

---

