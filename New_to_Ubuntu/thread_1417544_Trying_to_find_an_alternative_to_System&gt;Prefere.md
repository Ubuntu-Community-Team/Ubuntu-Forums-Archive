---
title: "Trying to find an alternative to System&gt;Preferences&gt;Sound"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by diablo75 on 2010-02-27
I recently removed PulseAudio because it was unable to support my sound card (Creative Labs SoundBlaster Audigy 2) as well as ALSA is able to and I'm much happier with Pulse gone now.  But removing it also removed the Sound Preferences Control Panel, which in the old days looked like this:

[IMG]http://www.ngohaibac.com/wp-content/uploads/2009/05/sound-preferences.png[/IMG]

I was wondering if there is a way to replace this, preferably with the version that appears in the screen shot above (or at least something that will let me set the system to default to ALSA instead of Pulse because it's no longer available.

I found a thread that's a couple of years old where someone asked a similar question and the best answer they got back was to install the gnome-control-center package, which looks pretty similar to the control panel you find in xfce if I'm not mistaken.  I tried it out myself but run into the same problem I do right now when I click on the sound icon.  Since I ran this program from the terminal, I did get an error output when I clicked on sound which someone might be able to use to help troubleshoot.  It said:

```
** (gnome-volume-control:5332): WARNING **: Connection failed, reconnecting...

```

And this just kept repeating so long as I let the "Waiting for sound system" dialog box to sit there; I clicked OK to cancel after so many failed attempts.

Anyone know how I might be able to get this working?

---

### Post by quixote on 2010-02-28
Synaptic has alsa-tools and alsa-tools-gui which I think give you at least some kind of graphical frontend, although I don't think it's the one in your screenshots.  Might be worth a try.

---

### Post by diablo75 on 2010-02-28
> **quixote said:**
> Synaptic has alsa-tools and alsa-tools-gui which I think give you at least some kind of graphical frontend, although I don't think it's the one in your screenshots.  Might be worth a try.

Thanks for the suggestion.

I checked it out just now and it looks like this is a small collection of a few tools that are meant for specific hardware components that I don't happen to have.  From Synaptic Package Manager:


(alsa-tools):
> A collection of console-based utilities for specific sound hardware:

 ac3dec - A free AC-3 stream decoder
 as10k1 - An assembler for the EMU10K1 (EMU10K2) DSP chip
 sbiload - OPL2/3 FM instrument loader for the ALSA sequencer
 us428control - Controller utility for Tascam US-X2Y

(alsa-tools-gui):
> A collection of GUI based ALSA utilities for specific sound hardware:

 echomixer - control tool for Echoaudio soundcards
 envy24control - control tool for Envy24 (ice1712) based soundcards
 hdspconf - GUI program to control the Hammerfall HDSP Alsa Settings.
 hdspmixer - tool to control the advanced routing features of the
             RME Hammerfall DSP.
 rmedigicontrol - control tool for RME Digi32 and RME Digi96 soundcards

The look of the control panel I have posted above isn't really important; I'd be willing to edit a text file if it did the job.  All I'm wanting to do change a global setting that some applications apparently seem to reference when trying to determine what sound system they should use when outputing audio, so I can have them use ALSA... because I think a few are trying to use PulseAudio because they just don't know any better.

---

### Post by quixote on 2010-03-02
I found this rather convoluted blogpost about getting Pulseaudio to shut up and go away: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/).  I'm not sure I'd follow all the commands listed, but some of them look like they could be useful.  There are several relevant to making sure ALSA is the default for audio.  (I realize it says "jaunty" but it seems to look the same on karmic, at least on my system.)

As for finding a more convenient GUI frontend, I'm still not sure how to go about that since the alsa-gui turns out not to be it. :(

---

### Post by diablo75 on 2010-03-03
Most of the blog post was useless but I found one snippet in there that I think did the trick.

At one point it says to edit the /usr/share/alsa/alsa.conf file and comment out one line with a #.

In that file there's a part that looks like this:

```
@hooks [
    {
        func load
        files [
            "/usr/share/alsa/pulse.conf"
            "/usr/share/alsa/bluetooth.conf"
            "/etc/asound.conf"
            "~/.asoundrc"
        ]
        errors false
    }
]
```

And you comment out the line that says /usr/share/alsa/pulse.conf

So it looks like this:

```
@hooks [
    {
        func load
        files [
#           "/usr/share/alsa/pulse.conf"
            "/usr/share/alsa/bluetooth.conf"
            "/etc/asound.conf"
            "~/.asoundrc"
        ]
        errors false
    }
]
```

Now when I hover my mouse over mp3 files I hear a preview like I used to.  Maybe that was actually working already, I don't know.  Totem, on the otherhand, still doesn't produce sound but that's no big deal to me.  I use VLC for everything anyway.

---

### Post by quixote on 2010-03-03
Hey, that's good to know.  Pulseaudio can be a real pest.  You'd think the devs would twig to the fact that there's a problem when, I swear, half the questions on the forums are about sound and multimedia problems.

---

