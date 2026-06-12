---
title: "Installing Firefox 3.5 (Final Released)"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by giry on 2009-07-06
If You Installed Ubuntu from repo you would find sth missing.
for me, if i login to facebook i lost chat feature (pop up chat)
so i seek for help and found this...
(**tested on kubuntu 9. 04 with KDE 4.3 RC1**)

Here&#8217;s a really quick way to get 3.5 running on your Kubuntu, Ubuntu, Xubuntu 9.04 system.
Open up Terminal (Applications > Accessories > Terminal) and run the following commands:

1.cd /tmp 
2.wget "http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US"
Note: Your download link may be different depending on your country and language. I got the link by clicking the download link, canceling the automatic download, right-clicking the &#8220;Your download should automatically begin in a few seconds, but if not, click here&#8221; link, and selecting Copy Link Location. 
3.tar xvf firefox-*.bz2 
4.sudo cp -r firefox /usr/lib/firefox-3.5 
5.sudo mv /usr/bin/firefox /usr/bin/firefox.old 
6.sudo ln -s /usr/lib/firefox-3.5/firefox /usr/bin/firefox-3.5 
7.sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox 
8.Close Firefox and then reopen. You should now be running Firefox 3.5.

If for whatever reason you&#8217;d like to switch back to your previous version of Firefox, simply run the following commands from Terminal:
1.sudo mv /usr/bin/firefox /usr/bin/firefox.bak 
2.sudo mv /usr/bin/firefox.old /usr/bin/firefox 
	

Notice how I even create a backup of the original firefox before replacing it. It is always a good idea to do this if you replace programs yourself. This way you won&#8217;t be likely to remove a binary or script that you won&#8217;t be able to get back easily.
Now that you are on Firefox 3.5, check out some awesome sites that show off some of the new capabilities.
3-D cubes built with standard HTML content, including the new native video component. 
Audio player built entirely with HTML, CSS, and Javascript. It doesn&#8217;t even use what we commonly think of as images, simply the new Canvas element. 
Video Washing Machine &#8211; Add a video to your site, crop it to fit in a circle, put a border around it, have rollover effects that change the filter on the video, and spin the whole thing as it plays. All of this with just the <video> element, CSS 3, SVG, and a bit of JavaScript. 
Add upload progress bars without the use of Flash or insane amounts of scripting. 
Create the illusion of a 3D voxel engine with an image and some creative SVG, scripting, and CSS. 
Apply textures to an animated model. 
Create a text shadow spotlight effect using Javascript and CSS. 
Web developers can now take advantage of custom typography using the new CSS rules. 
Sync page elements with the position in the video. Note that the graphs are canvas elements that are being drawn on. 
Use HTML elements to jump to different positions in audio.

[http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/]("http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/")

---

### Post by frenkel on 2009-07-06
How about installing the package from the ubuntu-mozilla-security ppa? A lot easier :P

---

### Post by lovinglinux on 2009-07-06
The 4 most popular methods of installation are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT).

I don't like the idea of your method saving firefox in the /usr/lib/firefox-3.5 directory, because it's the same directory used by the Shiretoko version. I'm not an expert, but I think it would be better to install it on the /opt/firefox directory as explained the first method of my thread (psychocats method). Besides, the pyschocats method also takes care of the necessary symbolic links, including the plugins.

Bottom line, I wouldn't recommend this method when there are others more efficient and simple. Please don't get me wrong, it's nothing personal. It's just that there is no need for more "alternative" solutions, because then people will come to the forum for help solving problems with Firefox 3.5 and there is a big mess of installations that are hard to troubleshoot ([see this thread as an example](http://ubuntuforums.org/showthread.php?t=1197505)).

> **giry said:**
> Notice how I even create a backup of the original firefox before replacing it. It is always a good idea to do this if you replace programs yourself. This way you won’t be likely to remove a binary or script that you won’t be able to get back easily.
Now that you are on Firefox 3.5, check out some awesome sites that show off some of the new capabilities.

Not really. You are not replacing Firefox 3.0 with this, you are just installing a new version in another directory and replacing the symlinks to launch it. Besides, if something goes wrong, all you need is to go to Synaptic and mark Firefox for re-installation. So why you would make a backup of the original Firefox?

The only thing that you should backup is the Firefox profiles, which are kept in your home directory even when you install new versions.

---

### Post by JoeNZ on 2009-07-06
If it is any help to anyone, I successfully installed Firefox 3.5 using Ubuntuzilla. Very easy to do, just followed their instructions. Done.

---

### Post by lovinglinux on 2009-07-06
> **JoeNZ said:**
> If it is any help to anyone, I successfully installed Firefox 3.5 using Ubuntuzilla. Very easy to do, just followed their instructions. Done.

Yep, it also worked like a charm. I tested all 4 methods described in my tutorial and they all work flawlessly, although I recommend methods 1 (pyschocats) and 2 (Ubuntuzilla).

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

