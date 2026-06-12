---
title: "Radio Tray Will Not Work."
date: 2011-06-23
forum: New to Ubuntu
---

### Post by P-rench on 2011-06-23
I'm pretty new to ubuntu and I just recently got a wubi verson of Ubuntu 10.04. Everything seems to be running good except for Radio Tray which I just installed yesterday. Everytime I add a new radio station I constantly get the same error "Your GStreamer Instalation is missing a plug-in" so yea, no radio station is working at the moment. I have combed through the internet pretty intensly looking for an answer and not much comes up. One of the main solutions I have come across is doing sudo apt-get install ubuntu-restricted-extras in the terminal. I did that and it didn't work, even after I restarted my computer. So at the moment I'm not sure what to do, either it is a plug-in issue or I'm just putting the URL in wrong somehow. This is the main URL I'm trying to get to work [http://www.wham1180.com/mediaplayer/?station=wham-am](http://www.wham1180.com/mediaplayer/?station=wham-am)    is this the wrong type of URL? Any help would be greatly appreciated!

---

### Post by wildmanne39 on 2011-06-23
> **P-rench said:**
> I'm pretty new to ubuntu and I just recently got a wubi verson of Ubuntu 10.04. Everything seems to be running good except for Radio Tray which I just installed yesterday. Everytime I add a new radio station I constantly get the same error "Your GStreamer Instalation is missing a plug-in" so yea, no radio station is working at the moment. I have combed through the internet pretty intensly looking for an answer and not much comes up. One of the main solutions I have come across is doing sudo apt-get install ubuntu-restricted-extras in the terminal. I did that and it didn't work, even after I restarted my computer. So at the moment I'm not sure what to do, either it is a plug-in issue or I'm just putting the URL in wrong somehow. This is the main URL I'm trying to get to work [http://www.wham1180.com/mediaplayer/?station=wham-am](http://www.wham1180.com/mediaplayer/?station=wham-am)    is this the wrong type of URL? Any help would be greatly appreciated!Hi, open software center and type restricted and it should bring them up and just click install.

---

### Post by P-rench on 2011-06-23
I'm also using Pulse Audio incase that might be causing a problem.

---

### Post by P-rench on 2011-06-23
Thanks for the reply. I opened software center, typed in restricted and it appears I already have ubuntu restricted extras installed. Any other ideas?

---

### Post by P-rench on 2011-06-24
Ok, so I think I had the wrong URL. In firefox browser I went to tools-->Page info--> then clicked the Media tab. The new URL I got is [http://www.wham1180.com/mediaplayer/CCB-20110309.swf](http://www.wham1180.com/mediaplayer/CCB-20110309.swf) which looks more right but when I loaded into radio tray I got a new error which is "GStreamer encountered a general supporting library error" So yea, still lost. Any ideas?

---

### Post by wildmanne39 on 2011-06-24
> **P-rench said:**
> Ok, so I think I had the wrong URL. In firefox browser I went to tools-->Page info--> then clicked the Media tab. The new URL I got is [http://www.wham1180.com/mediaplayer/CCB-20110309.swf](http://www.wham1180.com/mediaplayer/CCB-20110309.swf) which looks more right but when I loaded into radio tray I got a new error which is "GStreamer encountered a general supporting library error" So yea, still lost. Any ideas?Hi, I would complete remove the extra's including gstreamer by opening synaptic package manager, find the packages and mark for complete removal be right clicking on the package and selecting complete removal, then restart ubuntu and reinstall the packages.

---

### Post by P-rench on 2011-06-24
Bump

---

### Post by P-rench on 2011-06-24
Haven't come acrossed a solution yet but theres got to be another way to do this then to uninstall of the gstreamer packages. Any ideas?

---

### Post by Frogs Hair on 2011-06-24
It works for me and these are my Gstreamer plug-ins.

---

### Post by P-rench on 2011-06-24
I have all those plug-ins as well, still no go. Could you give me a couple examples of the URL's you use for your radio station? I'm thinken maybe I'm putting in the wrong URL or something.

---

### Post by Frogs Hair on 2011-06-24
Not having any problems connecting to and playing any stations available on that site  . If one of your Gsteamer libraries is not working you may have to reinstall the plug-ins  . I don't know what else to suggest since we both have the same plug-ins . I normally use Aol Radio and Last fm , Aol is a similar site as it offers access to many stations .

---

### Post by P-rench on 2011-06-24
Crud, well, looks like I'm gonna have to reinstall some plug ins. I'll let everyone know how this works out.

---

### Post by P-rench on 2011-06-24
alright well I uninstalled the main plug-ins that were mentioned in this thread and a few other ones, restarted my computer, re-installed all plug-ins plus any other gstreamer plug-ins that were available, restarted computer again, then opened Radiotray....and it still doesn't work. I'm so lost on this one right now. I literally have every possible gstreamer plugin installed right now and still radiotray does not work and gives me the same error messages. Anyone got some other ideas?

---

### Post by P-rench on 2011-06-24
Ok, the pre-installed radio station on radiotray are working now, which is a success, but the radio station I tried to add is still not working. I'm pretty sure I'm doing something wrong with the URL, but I'm not sure what. I'm using two different URL's  which are: 
[http://www.wham1180.com/mediaplayer/?station=wham-am](http://www.wham1180.com/mediaplayer/?station=wham-am) 

[http://www.wham1180.com/mediaplayer/CCB-20110309.swf](http://www.wham1180.com/mediaplayer/CCB-20110309.swf) 

Neither one of these URL's work in Radiotray for me and I'm not sure why. Would anyone would be willing to try out these URL's to see if they work in their radiotray? It would really help me pinpoint whether my issue is plug-in related or URL related.

---

### Post by P-rench on 2011-06-25
Alright apparently radiotray is supposed to be able to play ASX and I found a URL for the radiostation previously mentioned which is: [http://109.228.5.193/stream/5723/source.asx](http://109.228.5.193/stream/5723/source.asx) 
I added it to radiotray and still itdoes not work. I have no idea what the problem is. It seems like radiotray will only play the pre-installed radio stations because the other ones I keep trying to add just don't work. I'm at a loss of what to do right now and apparently I don't understand how this URL thing works since I can't get any of of the ones I add to work. If anyone has an answer It would be really appreciated.

---

### Post by P-rench on 2011-06-25
bump

---

### Post by kherring7383 on 2011-06-27
I checked out the Radio Tray website and here are the dependencies that are required. I don't know what version you have installed, but the most current is 06.3.


Radio Tray is programmed in Python and uses the following libraries::
GStreamer (python-gst >= 0.10) for audio processing
GTK2 (python-gtk2) for the user interface
Python lxml (python-lxml 2.1.5) for xml files processing
python-gobject (>= 2.18.0)
python-notify (>= 0.1.1) or in some distros notify-python
python-dbus (>= 0.83.0)

As for the stations, I use Shoutcast stations. You find a station and right-click and choose "Save link as" then paste it into Radio Tray and edit the Station Info.

Also, as an alternative, create a free Pandora account and install Pithos in Ubuntu that can be used to access your Pandora account.
 
Check out this link: [http://www.ubuntugeek.com/pithos-pandora-client-for-the-gnome-desktop-ubuntu-ppa-installation-instructions-included.html]("http://www.ubuntugeek.com/pithos-pandora-client-for-the-gnome-desktop-ubuntu-ppa-installation-instructions-included.html")

I use both Radio Tray and Pithos. The upside to a free Pandora account is commercial free radio. The downside is only 40hours a  month with the free account.

Hope this helps.

---

