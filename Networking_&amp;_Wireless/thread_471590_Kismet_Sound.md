---
title: "Kismet Sound"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by ronanmagee on 2007-06-12
Hi Guys,

I have Kismet up and running on Feisty using Kismet-2007-01-R1b.  Built, compiled and made ok.

My problem is the sounds in it.

I modifed the kismet.conf and kismet_ui.conf to set sounds to true, enable the different sounds and use aplay instead of play.

I still cant get sounds to work, yet all system sounds do.  Also, if I do aplay /usr/local/share/kismet/wav/newnewtork.wav it will play the sound manually.

I also have made sure the client doesnt have the sound muted.

Any ideas greatly appreciated.

Ronan

P.S Is there some compile option I have to set to get it to enable sounds?

---

### Post by tturrisi on 2007-06-12
```
# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=true
# Path to sound player
soundplay=/usr/bin/aplay
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=//usr/share/kismet/wav/new_network.wav
# Wepped new network
# sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=//usr/share/kismet/wav/traffic.wav
# Network junk traffic found
sound_junktraffic=//usr/share/kismet/wav/junk_traffic.wav
# GPS lock aquired sound
# sound_gpslock=//usr/share/kismet/wav/foo.wav
# GPS lock lost sound
# sound_gpslost=//usr/share/kismet/wav/bar.wav
# Alert sound
sound_alert=//usr/share/kismet/wav/alert.wav

```

my gui w/ white background and readable text:
```
# Kismet GUI config file

# Version of Kismet config
version=2004.10.R1

# Do we show the intro window?
showintro=false

# Gui type to use
# Valid types: curses, panel
gui=panel
# Server to connect to (host:port)
host=localhost:2501
# Network traffic decay (active/recent/inactive) and packet click rate - increase
# this if you are doing prism2 channel hopping.
decay=3
# What columns do we display?  Comma seperated.  Read the documentation for what 
# columns are valid.
columns=decay,name,type,wep,channel,packets,flags,ip,size
# What columns do we display for clients?  Comma seperated.
clientcolumns=decay,type,mac,manuf,data,crypt,size,ip,signal,quality,noise
# Does the GUI use sound?
# NOT to be confused with "sound" option later, which is for the SERVER to make
# noise on whatever host it's running on.
sound=true
# Path to sound player
soundplay=/usr/bin/aplay
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=//usr/share/kismet/wav/new_network.wav
# Wepped new network
# sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=//usr/share/kismet/wav/traffic.wav
# Network junk traffic found
sound_junktraffic=//usr/share/kismet/wav/junk_traffic.wav
# GPS lock aquired sound
# sound_gpslock=//usr/share/kismet/wav/foo.wav
# GPS lock lost sound
# sound_gpslost=//usr/share/kismet/wav/bar.wav
# Alert sound
sound_alert=//usr/share/kismet/wav/alert.wav

# Do we auotmatically make a group for probed networks or do we show them
# amidst other networks?
autogroup_probe=true
# Do we autogroup data-only networks?
autogroup_data=true
# Do we autogroup adhoc networks?
autogroup_adhoc=true

# Display battery status?
apm=true

# Does the GUI talk to us with Festival?
speech=false
# Where is festival located for the GUI?
festival=/usr/bin/festival
# Are we using festival light?  If so, point the above "festival" path to the
# "flite" binary.
flite=false
# How do we speak?  Valid options:
# speech    Normal speech
# nato      NATO spellings (alpha, bravo, charlie)
# spell     Spell the letters out (aye, bee, sea)
speech_type=nato
# speech_encrypted and speech_unencrypted - Speech templates
# Similar to the logtemplate option, this lets you customize the speech output.
# speech_encrypted is used for an encrypted network spoken string
# speech_unencrypted is used for an unencrypted network spoken string
#
# %b is replaced by the BSSID (MAC) of the network
# %s is replaced by the SSID (name) of the network
# %c is replaced by the CHANNEL of the network
# %r is replaced by the MAX RATE of the network
speech_encrypted=New network detected, s.s.i.d. %s, channel %c, network encrypted.
speech_unencrypted=New network detected, s.s.i.d. %s, channel %c, network open.

# Simple borders (use - and | instead of smooth vertical and horizontal
# lines.  This is required on Zaurus, and might be needed elsewhere if your
# terminal doesn't display the border characters correctly.
simpleborders=false

# Colors (front, back) of text in the panel front.  Valid colors are:
# black, red, yellow, green, blue, magenta, cyan, white
# optionally prefixed with "hi-" for bold/bright colors, ie
# hi-red, hi-yellow, hi-green, etc.

# Enable colors?  
color=true
# Background
#backgroundcolor=
# Default text
textcolor=hi-black
# Window borders
bordercolor=black
# Titles
titlecolor=hi-black
# GPS and APM info
monitorcolor=hi-black
# WEP network color
wepcolor=hi-red
# Factory network color
factorycolor=hi-green
# Open color
opencolor=hi-blue
# Decloaked network color
cloakcolor=hi-magenta

```

---

### Post by ronanmagee on 2007-06-12
Cheers for your post tturrisi.  Your config file is similar to what I have, except mines has the ${prefix} variable.  I presume this is just /usr/local.

As all my files are correctly located I still dont understand why its not working.

Any ideas?

```

#Kismet_ui.conf

sound=true
# Path to sound player
soundplay=/usr/bin/aplay
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=${prefix}/share/kismet/wav/new_network.wav
# Wepped new network
sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=${prefix}/share/kismet/wav/traffic.wav

```

---

### Post by ronanmagee on 2007-06-12
Got it sorted ... turns out the $perfix var wasnt set so had to manually set it to /usr/local/share/kismet/wav/newnetwork.wav and so on for each of the sound files.

Sorry for being so slow on this one ... I thought I'd already tried that ...

Ronan

---

### Post by tturrisi on 2007-06-13
lol!
Just be careful w/ your pcm volume setting.  Because I'm on a laptop, I usually keep my volume set high so I can hear sound in videos & music.  Then I run kismet and get blasted.  (not exactly the thing I want to have happen when in a coffee shop or public hotspot!)

---

