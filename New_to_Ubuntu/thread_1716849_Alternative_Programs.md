---
title: "Alternative Programs"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by JamesBartlett on 2011-03-29
Hi guys, I've recently switched from Windows 7 to Ubuntu, and there were some Programs I used a lot. Can anyone tell me how to get them on Ubuntu or where to find similiar alternatives:

FL Studios
Virtual DJ
Skype
Firefox 4 (I have 3.6)
MS Office Outlook
utorrent

Thanks guys

---

### Post by owiknowi on 2011-03-29
maybe for some programs you could use ubuntu studio instead of ubuntu:
[http://ubuntustudio.org/](http://ubuntustudio.org/)

you can also install it from within your current ubuntu installation through synaptic.

some of the software you are looking for can be found in the extra repositories?

evolution for outlook
transmission for qtorrent
 don't know the rest but i've seen skype at work under tux

---

### Post by owiknowi on 2011-03-29
and check out this post on skype:
[http://ubuntuforums.org/showthread.php?p=10613347#post10613347](http://ubuntuforums.org/showthread.php?p=10613347#post10613347)

---

### Post by mastablasta on 2011-03-29
> **JamesBartlett said:**
>  alternatives:
 
Skype
Firefox 4 (I have 3.6)
MS Office Outlook
utorrent

 
don't know for the first two, but: 
 
Skype - skype has a linux client. google it, download the .deb file from skype for linux site (i think it will say for ubuntu 8.10 or 9.04 or something ) and double click it to install.
Firefox 4 (I have 3.6) : have a look here on how to replace FF3.6 with 4 (you can copy commands line by line to terminal): [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)
 
MS Office Outlook - Outlook can be run via WINE or you can use Evolution, Thunderbird or Kmail as e-mail client. does it have to be compatible with MS outlook? i am not a big fan of it and use Thunderbird even under windows...
 
utorrent - deluge or ktorrent, default torrent client is transmission (simple and it works). there are more out there.

---

### Post by Dutch70 on 2011-03-29
Hi and welcome to UF

 You can also google for "linux equivalent of *your_app*" 

Here are some links that you may find useful.
[[COLOR="Blue"]http://www.osalt.com/[/COLOR]]("http://www.osalt.com/")
[[COLOR="Blue"]http://www.knowliz.com/2009/08/25-must-have-ubuntu-linux-applications.html[/COLOR]]("http://www.knowliz.com/2009/08/25-must-have-ubuntu-linux-applications.html")
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=382137&highlight=making+website&page=3[/COLOR]]("http://ubuntuforums.org/showthread.php?t=382137&highlight=making+website&page=3")

---

### Post by mcduck on 2011-03-29
LMMS has pretty similar interface to FL Studio. You should feel quite at home with it.

VirtualDJ could be replaced by Mixxx. For more professional work, I've understood that Final Scratch works with Linux as well.

Skype for Linux is, well, Skype. :D

Firefox is rather easy to upgrade, like others have already pointed out.

uTorrent would easily be replaced by Transmission (installed by default) or Deluge.

The closest equivalent for Outlook would be Evolution. It's already installed. Don't except full compatibility with Outlook, though, Microsoft doesn't play well with others.

---

### Post by d3v1150m471c on 2011-03-29
firefox4 you can install firefox4 :)
for skype you can install the .deb of skype
evolution vs ms outlook
transmission-daemon and transmission for torrents

---

### Post by JamesBartlett on 2011-03-29
Well so far so good guys,
Evolution is sorting my email ok,
transmission is doing my torrenting fine,
I've gotten FF4 up and running,
AS for LMMS, I'm getting as far as here: [https://launchpad.net/~tobydox/+archive/lmms](https://launchpad.net/~tobydox/+archive/lmms) but then I'm coming across Ubuntu jargon which is a new language to me...
As for mixxx, I was getting this when using terminal when following the Ubuntu instructions at [http://www.mixxx.org/download.php:](http://www.mixxx.org/download.php:)
james@james-ubuntu:~$ sudo apt-get install mix libportaudio2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mix
james@james-ubuntu:~$ ^C

Thanks so far for your help guys!

---

### Post by mcduck on 2011-03-29
LMMS:

```
sudo add-apt-repository ppa:tobydox/lmms
sudo apt-get update
sudo apt-get install lmms
```

..and Mixxx:
```
sudo add-apt-repository ppa:mixxx/mixxx
sudo apt-get update
sudo apt-get install mixxx libportaudio2
```
(note that it's called "mixxx", not "mix". ;). And also the latest version is already in the official repositories for Ubuntu 10.10, so you only need to add the PPA if you are running older Ubuntu release and want the latest versions of Mixxx. At least some version of LLMS should also be available in the official repositories, so once again the PPA is only required if you want the latest version.)

---

### Post by kevinamadeus2 on 2011-03-29
You need to add the PPA before you can install, otherwise the software cannot be found in the 'standard list of software'

```
sudo add-apt-repository ppa:mixxx/mixxx
sudo apt-get update
sudo apt-get install mixxx libportaudio2
```

According to the website you posted.

---

### Post by JamesBartlett on 2011-03-29
I have done exactly those instructions into terminal for Mixxx, when I install it from the software centre it says: installArchives() failed:

---

### Post by JamesBartlett on 2011-03-29
as for lmmg when I try to install using terminal it eventually says:
E: Internal Error, Could not perform immediate configuration (2) on mountall

---

### Post by JamesBartlett on 2011-04-01
Right, I ended up reinstalling Ubuntu for other reasons, and have installed Mixxx and LMMS.

Still two problems, I might be being picky, but Mixxx is a little bit crap (no disrespect to whoever designed it, its a far better job than I could ever do) and LMMS is only showing the splash screen but never actually satarting...

---

### Post by Clockmender on 2011-04-01
Hi

For Fruity Loops - I switched to LMMS but found the sustain pedal does not work so now use Rosegarden (Install with Synaptic) maybe one day those nice people who write LMMS will fix the "god damn" Sustain Pedal function please pretty please...:mad: Then I can access multiple Soundfonts, something you can't do with Rosegarden or I haven't found the way yet...:redface: -  for more info on my setup see my post at:

[http://ubuntuforums.org/showthread.php?p=10249260#post10249260](http://ubuntuforums.org/showthread.php?p=10249260#post10249260)

As for Outlook, I use Thunderbird from Mozilla - best mail client I ever found, dead easy to setup and full of functionality including web browsing, tabbed mail and mail Bookmarks through add-ons. There are loads of add-ons for extra functionality

Transmission is a good Peer-to-Peer client, not that I or you would ever be using it to download copyright material of course...[-X

Cheers

Clock

Oh by the way - check your sound card clock rate if LMMS only displays splash screen then vanishes, on my E-MU 0404 it must be set to 48000 or it won't work, also check you are not running too many sound systems - stick to JACK or ALSA and use Patchage and KMidimon to see what is going on and what is connected to what and how.

And don't forget that you have to put a penny in the swear box if you mention Wind'ohs or any Microsoft product by name in here unless you are being derogatory.

---

### Post by JamesBartlett on 2011-04-01
> **Clockmender said:**
> Hi

For Fruity Loops - I switched to LMMS but found the sustain pedal does not work so now use Rosegarden (Install with Synaptic) maybe one day those nice people who write LMMS will fix the "god damn" Sustain Pedal function please pretty please...:mad: Then I can access multiple Soundfonts, something you can't do with Rosegarden or I haven't found the way yet...:redface: -  for more info on my setup see my post at:

[http://ubuntuforums.org/showthread.php?p=10249260#post10249260](http://ubuntuforums.org/showthread.php?p=10249260#post10249260)

As for Outlook, I use Thunderbird from Mozilla - best mail client I ever found, dead easy to setup and full of functionality including web browsing, tabbed mail and mail Bookmarks through add-ons. There are loads of add-ons for extra functionality

Transmission is a good Peer-to-Peer client, not that I or you would ever be using it to download copyright material of course...[-X

Cheers

Clock

Oh by the way - check your sound card clock rate if LMMS only displays splash screen then vanishes, on my E-MU 0404 it must be set to 48000 or it won't work, also check you are not running too many sound systems - stick to JACK or ALSA and use Patchage and KMidimon to see what is going on and what is connected to what and how.

And don't forget that you have to put a penny in the swear box if you mention Wind'ohs or any Microsoft product by name in here unless you are being derogatory.
Haha, I'm not going to completely tar Windows (penny), although I am far more impressed with Ubuntu. ;)
But I am (was) a keen gamer, and for me Ubuntu just doesn't cut it for games.

The kind of stuff I was doing on FL, I can live without sustain pedals, although I feel for ye bud. I've gotten my torrenting sorted (qBittorrent) for my *strictly legal* downloading.

I have set up Thunderbird thanks to you, I had totally forgotten about it after using it back in the days when MS Vista (penny) was shiny and new, but its doing the job nicely. Good old Mozilla, there really ain't no finer diner.

I'm guessing from your username and what you were saying about the soundcard you're an over-clocker? To be honest mate, I wouldn't have known how to check clockspeeds fot the overall system on a Windows (penny) OS, let alone a mere component on a less familiar OS. Is there a minimum clockspeed you'd recommend? My soundcard worked fine on Win 7 (penny), and how do you check?

And the only sound related program I've been running is RhythmBox (hardly taxing?) for a bit of background tuneage. - I'm not likely to be running that while runng LMMS...

And lastly, what's Synaptic? (sincere n00b apologies ;))

---

### Post by Clockmender on 2011-04-08
Hi sorry it's taken a while to reply...Kitchens to paint, etc.

"Clockmender" is because I repair old Grandfather clocks, anniversary clocks, well anything with a pendulum or other escapement really - sad but someone has to keep these old timepieces going, anyway I digress.

Glad you've sorted Thunderbird.

As for setting the clock speed of your sound card simply open a terminal window "Applications" - "Accessories" - "Terminal" and type [COLOR="Red"]alsamixer[/COLOR] and press return. You can then use the Left and Right arrow keys to get to your sound cards clock speed (if you have many sound cards use F6 to select the one you want. Then use the Up and Down arrow keys to change the clock speed. Then press Esc to exit followed by typing [COLOR="Red"]alsactl store[/COLOR] to save the changes permanently. You can do all sorts of wonderful things like set the internal volume levels, etc. while you are there. Best clock speed for my E-MU is 48000 but check the forums for your own.

No sustain pedal is a big issue for me as I play live and you cannot do that without a sustain pedal but Rosegarden sorts all this for now. I used to use [COLOR="Blue"]Reason[/COLOR] from [COLOR="Blue"]Propellerheads[/COLOR] in Sweden (see [http://www.propellerheads.se/](http://www.propellerheads.se/)) when I had Wind'ohs (spit) and nothing on Linux is quite as good yet, but we all live in hope.

I started using Rythmbox to replace iTunes - not so good but heyho. Then I used [COLOR="Blue"]Banshee[/COLOR] - much better. Now I use [COLOR="Blue"]Squeezebox Server[/COLOR] and [COLOR="Blue"]SqueezePlay[/COLOR] as I stream music all around my house and control the whole system via [COLOR="Blue"]iPeng[/COLOR] app (£5.99 in the UK) on my iPhone - brilliant.

You can Google all these things and see for yourself what they do. Basically you put Squeezebox Server on your PC with all the music then SqueezePlay on all the other PC's where you want the music to come out - I use an old laptop connected to my surround sound system and my house wifi - very good and very cheap! and a Squeezebox Boom (see [http://www.logitech.com/en-gb/speakers-audio/wireless-music-systems/devices/4707](http://www.logitech.com/en-gb/speakers-audio/wireless-music-systems/devices/4707)) for where ever I happen to be where there is no PC.

For the Synaptic Package Manager to load software, click on "System" - "Administration" - "Synaptic Package Manager" and when it has loaded just type in the name of the product you want to load into the search box - then Right Mouse Click the product in the search results and click "Mark for Installation" - this ensures all dependencies are loaded and that you use authorised software sources, then click "Apply" icon. Don't try to compile and install packages yourself at this stage - you may screw something up [COLOR="Magenta"]"Synaptic Rules for noobies"[/COLOR]

To get Squeezebox server go to "Settings" - "Repositories" then select the "Other Software" tab and click "Add" then enter "http://debian.slimdevices.com" in the URL, "stable" in the Distribution and "main" in the Components. You can do this easily by adding "http://debian.slimdevices.com stable main" in the APT input line. Close the dialogue then click the "Reload" Icon and it will be there! Once loaded open a browser (Like Firefox - well only Firefox really teehee) and type in "http://[name of your pc]:9000/" in my case that would be: [http://beastie:9000/](http://beastie:9000/) (it's a good idea to bookmark this page so you don't forget it!) Click the settings on the bottom right and then you can do all the setup and scan your music files, (I can help here if required)

You don't have to apologies for being a noobie - everyone was one once!:p

Cheers

Clock

PS as a last resort for LMMS if it aint working - try reloading it with Synaptic - you may be missing some dependencies - let me know how you get on.


*[FONT="Comic Sans MS"][COLOR="Orange"]If at first you don't succeed, curl up in the corner and cry....[/COLOR][/FONT]*

---

