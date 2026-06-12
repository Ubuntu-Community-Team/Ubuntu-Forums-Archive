---
title: "HOW TO: HDMI Sound on Eeebox 1501p"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by androssofer on 2011-07-22
This has bugged me for a while now. after lots of attempts and pain i finally got my HDMI sound working on my eeebox! 

after reading this:

[http://forum.xbmc.org/archive/index.php/t-86333.html](http://forum.xbmc.org/archive/index.php/t-86333.html)

i was able to get it working, it was done by changing my HDA-Intel.conf.

```
sudo gedit /usr/share/alsa/cards/HDA-Intel.conf

```

and pasting this is in:

```
#
# Configuration for the Intel HD audio (ICH6/ICH7)
#

<confdir:pcm/front.conf>

HDA-Intel.pcm.front.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type softvol
	slave.pcm  "remap-surround71"
		
	control {
		name "PCM Playback Volume"
		card $CARD
	}
}	

# default with dmix+softvol & dsnoop
HDA-Intel.pcm.default {
	@args [ CARD ]
	@args.CARD {
		type string
	}

       type asym
        playback.pcm {
                type plug
                slave.pcm {
                        type softvol
                        slave.pcm "remap-surround71"
                        control {
                                name "PCM Playback Volume"
                                card $CARD
                        }
                }
        }

	capture.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dsnoop:" $CARD ]
			}
			control {
				name "Digital Capture Volume"
				card $CARD
			}
			min_dB -30.0
			max_dB 30.0
			resolution 121
		}
		# to avoid possible phase inversions with digital mics
		route_policy copy
	}
	hint.device 0
}

<confdir:pcm/surround40.conf>
<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>
<confdir:pcm/surround71.conf>

HDA-Intel.pcm.surround40.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround51.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround71.0 cards.HDA-Intel.pcm.front.0

<confdir:pcm/iec958.conf>

HDA-Intel.pcm.iec958.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type asym
	playback.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Playback Default"
				lock true
				preserve true
				value [ $AES0 $AES1 $AES2 $AES3 ]
			}
			{
				name "IEC958 Playback Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	capture.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Capture Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	hint.device 1
}

<confdir:pcm/hdmi.conf>

HDA-Intel.pcm.hdmi.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type hooks
	slave.pcm {
		type plug
		slave.pcm "remap-surround71"
	}
	hooks.0 {
		type ctl_elems
		hook_args [
		{
			name "IEC958 Playback Default"
			lock true
			preserve true
			value [ $AES0 $AES1 $AES2 $AES3 ]
		}
		{
			name "IEC958 Playback Switch"
			lock true
			preserve true
			value true
		}
		]
	}
	hint.device 3
}

<confdir:pcm/modem.conf>

HDA-Intel.pcm.modem.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type hw
	card $CARD
	device 6
	hint.show off
}

```

then editing my asound.conf:

```
sudo gedit /etc/asound.conf
```

and paste this in:

```
pcm.!hdmi-remap {
type asym
playback.pcm {
type plug
slave.pcm "remap-surround71"
}
}

pcm.!remap-surround71 {
  type route
  slave.pcm "hw:1,7"
  ttable {
    0.0= 1
    1.1= 1
    2.4= 1
    3.5= 1
    4.2= 1
    5.3= 1
    6.6= 1
    7.7= 1
  }
}
```

****note*** the line tht is hw:1,7 should be set to hw:3,0 for other HDMI Nvidia devices... (according to the link listed above)

then run alsamixer

```
alsamixer
```

then press F6 and select the HDMI card, then use the accross arrows to select the different "S/PDIF" and press 'M' if they say "MM" below them. so all the "S/PDIF" should have "00" under them. Sound should work now :)


then open up sounds preferences and check that High definition card is selected on the output tab...

addition: my flash videos sounds plays fine :)

---

