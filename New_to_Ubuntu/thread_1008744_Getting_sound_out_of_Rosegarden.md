---
title: "Getting sound out of Rosegarden"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by BigRicky on 2008-12-11
I'm a Windows user, and Linux enticed me over with some cool (free!) programs.  I compose music as a hobby, and Rosegarden is really why I installed Linux.  (I have been using Ubuntu for three days now.)  I knew I was in for a ride when Rosegarden's website said that you had to compile the program.  I know enough about such things to know that compiling a program is way beyond my knowledge and experience, so I was really grateful when I was able to get it installed with Synaptic Package Manager.  

Then the fun began.  It said I needed a Jack server, so after a bit of research I found out how do it, and got that running using qjackctl.  Then I needed Sox, which I got with the Add/Remove Applications application, and I thought I was set.  But no sound.  This was yesterday morning, and since then I have been trying to figure this out.  Some guy said he got it running with Timidity++, which I had already installed because as a composer I *have* to have a way to listen to MIDIs.  How you can get Rosegarden to run with Timidity, I haven't the foggiest, so I gave up on that idea pretty quickly when I realized there wasn't any sort of guide and I couldn't figure it out.  Then I found [_this_](http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html) guide, and I don't know whether it's been helpful or not, as I still don't have any sound.  So following that guide, I now have QSynth running and using the Fluid R3 GM soundfont. 

I have my JACK connections the same as he does:  [_His connections_](http://rosegarden.sourceforge.net/tutorial/pixmaps/qjackctl-connections.png), [_my connections_](http://i106.photobucket.com/albums/m246/El_Ornitorrinco/idunnojack-1.png).  But mine says "System" instead "ALSA."  Is that the problem, or have I skipped something else?

Thanks much for any help,
Ricky

---

### Post by evilkastel on 2008-12-11
YOu might need to get alsa i believe... check synaptic for alsa. (its a sound output i believe). Also you might have to make your ports run trough alsa, but that should be easy once you have alsa. let me know if further problems appear.

---

### Post by unf4b1x on 2008-12-11
> **BigRicky said:**
> I'm a Windows user, and Linux enticed me over with some cool (free!) programs...  But no sound...

Hey Ricky, I don't know about any of Rosegarden or Timidity++ but upon googling I found out they are applications for musicians and the like.

Now, since I also got the problem of having NO SOUND trying to open a flash video or mp3s as I started my linux box and I don't know if this could help you too but anyhow here's what I did:

I opened APPLICATIONS > ADD/REMOVE > select SOUNDS & VIDEO then select ALL AVAILABLE APPLICATIONS from the "Show:" menu > tick the GStreamer plugins that has a popularity of 5 stars or whatever GStreamer plugins you need > APPLY CHANGES (you need an active Internet connection.) 

goodluck!

---

### Post by markbuntu on 2008-12-11
Here are some linsk for you to get jack and rosegarden working

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

### Post by BwackNinja on 2008-12-11
I have rosegarden set up with Qsynth and fluidsynth and the problem you are having is probably that the playback device in rosegarden is set to the default, which is the alsa midi passthrough, which isn't very helpful.

An easy way to get past this is to go to the alsa tab in your connections dialog and connect the midi passthrough to fluidsynth.

If that didn't work, then you can check if fluidsynth is the problem. To check if fluidsynth is doing its job, you can install pmidi ```
sudo apt-get install pmidi
``` and then do ```
aconnect -i -o
``` which will give you the inputs and output connections with numbers look for "client ###: fluidsynth" and type ```
pmidi -p ###:0 your-midi-file.mid
``` replacing "###" with the number you saw next to fluidsynth client with the aconnect command and "your-midi-file.mid" with any midi file you have (easiest in the current directory.) If you hear sound, then fluidsynth is not your problem, and its configuration in rosegarden that's giving you problems.

---

### Post by BigRicky on 2008-12-15
evilkastel: I checked, and ALSA is installed, so that's not the problem.  

unf4b1x: Thanks, but MP3s work fine in RythmBox, that isn't the problem.

markbuntu: Those JACK tutorials were what I needed!  I didn't understand how the programs interacted with each other, but once I did, hooking up Rosegarden to QSynth was simple.  All I had to do was go to the ALSA tab in JACK, go to the Output area and open up the Rosegarden tab, and select "General MIDI" and then click on "Fluid Synth" in the "Input" area and then press the "connect" button, and voila!  Sound in Rosegarden!

The sound is quite horrible, and I get a bajillionty-two xruns, so I'm going to go invest another twenty hours in that and see if I can't get my program to make actual music.  And then after that...  Learning how to use VSTis.  Those are different threads, though.

Thanks, everyone, for your help and time!

---

### Post by Lorin Ricker on 2008-12-16
Ricky:  As one composer to another, you might look at and consider trying [Ubuntu Studio]("http://ubuntustudio.org"), a distro built specifically for sound, multi-media, music, video, graphics, and folks just like us! It generally tracks the mainline Ubuntu releases, and HH 8.10 is out.  See also the [Ubuntu Studio Wiki]("https://wiki.ubuntu.com/UbuntuStudio") pages, [Installation here]("https://help.ubuntu.com/community/UbuntuStudio/Installation"), [FAQs here]("https://help.ubuntu.com/community/UbuntuStudio/FAQ").

Things like Rosegarden, Audacious, Audacity, Ardour, MusE, MuseScore, Jack EQ, Jack Timemachine, Jack Control (etc.), ALSA support, QSynth, and much, much more, are already pre-built and installed in Studio.  Pre-built video tools include Kino, Open Movie Editor, and Stopmotion; the Gimp is here, too.  All the usual player suspects are here, as well as ripping and burning tools (Brasero, etc.).

Due to several lucky coincidences last summer, I was lucky enough to buy a pre-built, pre-installed, professional quality system, a [STUDIO]("http://eracks.com/products/Desktops/config?sku=STUDIO") (an open source audio workstation) from [eRacks.com]("http://eracks.com"), a systems builder/supply house in Orange, CA.  Great folks, fantastic service and quality!  (I liked 'em so much that I also bought 2 DESQ desktop systems for my wife and daughter -- we're nearly 100% Linux/Ubuntu now.)

If a pre-built system is not for you (yet), do note that Ubuntu Studio is available as a 32/64-bit build and download -- a 64-bit CPU runs it best, plenty of RAM and big disks are a plus for a serious music machine.  A Studio box makes a dandy general-purpose system, too -- I'm using it for all sorts of daily applications: email, OOo, Internet and more... here's the [Package List]("https://wiki.ubuntu.com/UbuntuStudio/PackageList"); it's big!

Since you're only a few days into Ubuntu, you'd not loose much time/effort by (re)installing Ubuntu Studio... certainly beats the config-hassles and build/compiles you're currently struggling with.  The [FAQ says]("https://help.ubuntu.com/community/UbuntuStudio/FAQ") that yes, you can "install onto an existing [Ubuntu] installation."  Just a suggestion.

Sorry I can't offer much help or experience with your specific config problems -- Since on my box, it all "just works", I've not had to pursue much trouble-shooting with these apps.  Best of luck!

-- Lorin

---

