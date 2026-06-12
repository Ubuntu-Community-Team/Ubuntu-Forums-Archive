---
title: "Can't get Sony mdr 10rbt headset to work in hsp profile with microphone"
date: 2019-08-29
forum: Networking &amp; Wireless
---

### Post by tominto on 2019-08-29
Hello.  I have a pair of Sony mdr 10rbt  bluetooth headphones, which I've been using for some time as headphones to listen to music and all is well.  But I would also like to use them as a headset with the microphone for skype calls.  However when I try to set them up with the hsp profile in sound settings, I get no sound at all and after a short time they disconnect.  I've done some research online but can't seem to find anything that will work.  I'm using Ubuntu 18.04   Anyone have any ideas?

---

### Post by tominto on 2019-09-08
Still having trouble with this.  My computer has a bluetooth/wifi pcie card.  Could this be the problem?  Maybe it's something to do with pulseaudio or bluez?  I can aconnect using A2DP profile, but hsp/hfp profiles don't work at all.

---

### Post by tominto on 2019-09-17
Still having problems with this and I've come to the conclusion that the problem is with the wifi/bluetooth chip in my computer. It's an AC 7260 mpcie bluetooth/wifi controller.  I tested out my headset using a borrowed Plugable bluetooth usb and it works using hsp/hfp profile.  
I'm running Ubuntu 18.04 with the latest official drivers/firmware for the 7260 and I'm using blueman 2.0.5 to connect to the headset.

---

### Post by mörgæs on 2019-09-17
If this is the problem you could ask for your thread to be moved to the networking forum.

---

### Post by tominto on 2019-09-18
Yes, I would like this to be moved to the networking forum.  I think it would be more helpful

Also, here is some output that might be useful.  I ran this while I had my headset connected in hsp profile.  It disconnected a short time later.
```

pacmd list-sinks
2 sink(s) available.
    index: 0
	name: <alsa_output.pci-0000_00_14.2.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9039
	volume: front-left: 16169 /  25% / -36.47 dB,   front-right: 16169 /  25% / -36.47 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 0
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
	card: 1 <alsa_card.pci-0000_00_14.2>
	module: 8
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC887-VD Analog"
		alsa.id = "ALC887-VD Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "1"
		alsa.card_name = "HD-Audio Generic"
		alsa.long_card_name = "HD-Audio Generic at 0xfea60000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:14.2"
		sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1022"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD]"
		device.product.id = "780d"
		device.product.name = "FCH Azalia Controller"
		device.form_factor = "internal"
		device.string = "front:1"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC887-VD"
		alsa.components = "HDA:10ec0887,1462d913,00100302"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-output-lineout: Line Out (priority 9900, latency offset 0 usec, available: yes)
			properties:
				
		analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-headphones"
	active port: <analog-output-lineout>
  * index: 18
	name: <bluez_sink.57_D3_98_0A_98_59.headset_head_unit>
	driver: <module-bluez5-device.c>
	flags: HARDWARE HW_VOLUME_CTRL LATENCY 
	state: RUNNING
	suspend cause: 
	priority: 9050
	volume: mono: 37789 /  58%
	        balance 0.00
	base volume: 65536 / 100%
	volume steps: 16
	muted: no
	current latency: 0.00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 29
	sample spec: s16le 1ch 8000Hz
	channel map: mono
	             Mono
	used by: 1
	linked by: 1
	fixed latency: 28.00 ms
	card: 10 <bluez_card.57_D3_98_0A_98_59>
	module: 38
	properties:
		bluetooth.protocol = "headset_head_unit"
		device.intended_roles = "phone"
		device.description = "MDR-10RBT"
		device.string = "57:D3:98:0A:98:59"
		device.api = "bluez"
		device.class = "sound"
		device.bus = "bluetooth"
		device.form_factor = "headset"
		bluez.path = "/org/bluez/hci0/dev_57_D3_98_0A_98_59"
		bluez.class = "0x240404"
		bluez.alias = "MDR-10RBT"
		device.icon_name = "audio-headset-bluetooth"
	ports:
		headset-output: Headset (priority 0, latency offset 0 usec, available: unknown)
			properties:
				
	active port: <headset-output>
```

---

### Post by DuckHook on 2019-09-24
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

