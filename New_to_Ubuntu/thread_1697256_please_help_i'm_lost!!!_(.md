---
title: "please help i'm lost!?!?! :("
date: 2011-02-28
forum: New to Ubuntu
---

### Post by adduds on 2011-02-28
acer aspire 5820TG i5 460m
ati radeon hd 5650

i'm tryin' to get catalyst control centre up and working because i wanna play counterstrike source and i'm sooo lost

I did these commands

```
sudo apt-get remove --purge xserver-xorg-video-radeon
wget http://www2.ati.com/drivers/linux/at...x86.x86_64.run
chmod +x ati-driver-installer*.run
sudo ./ati-driver-installer*.run
Go through installation.
sudo aticonfig --initial
sudo reboot
```

when i go to ccc in the system preferences menu it just says "initialization error no ati driver or it is not working properly"

when i booted up i only got a black screen

lspci -v

both are listed? flgrx and radeon?

```
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 035d
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at dc400000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at dc440000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: fglrx, radeon

```

---

### Post by TechWiz2100 on 2011-02-28
Only Radeon is being used according to your report however you may want to remove fglrx just to be on the safe side. Also check to see if your card needs special xorg.conf edits.

---

### Post by sandyd on 2011-02-28
> **adduds said:**
> acer aspire 5820TG i5 460m
ati radeon hd 5650

i'm tryin' to get catalyst control centre up and working because i wanna play counterstrike source and i'm sooo lost

I did these commands

```
sudo apt-get remove --purge xserver-xorg-video-radeon
wget http://www2.ati.com/drivers/linux/at...x86.x86_64.run
chmod +x ati-driver-installer*.run
sudo ./ati-driver-installer*.run
Go through installation.
sudo aticonfig --initial
sudo reboot
```when i go to ccc in the system preferences menu it just says "initialization error no ati driver or it is not working properly"

when i booted up i only got a black screen

lspci -v

both are listed? flgrx and radeon?

```
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 035d
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at dc400000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 3000 [size=256]
    Expansion ROM at dc440000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: fglrx, radeon

```
does
```

modprobe fglrx
```
output anything?

---

### Post by adduds on 2011-02-28
> **sandyd said:**
> does
```

modprobe fglrx
```
output anything?
no it doesn't..?

```

toews@kidlapp:~$ modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.35-22-generic/kernel/drivers/char/drm/fglrx.ko): Operation not permitted
toews@kidlapp:~$ sudo modprobe fglrx
[sudo] password for toews: 
toews@kidlapp:~$ sudo modprobe fglrx
toews@kidlapp:~$ 

```

when i went to synaptic and searched fglrx both packages aren't installed..? (fglrx and fglrx-amdcccle)

what is checked off is "xserver-xorg-video-radeon" but it states 

"Note that this is not the same as the ATI-provided, binary-only, 'fglrx'
driver, which provides additional 3D functionality for some newer Radeon
cards, but is not supported."

---

### Post by sandyd on 2011-02-28
> **adduds said:**
> no it doesn't..?

```

toews@kidlapp:~$ modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.35-22-generic/kernel/drivers/char/drm/fglrx.ko): Operation not permitted
toews@kidlapp:~$ sudo modprobe fglrx
[sudo] password for toews: 
toews@kidlapp:~$ sudo modprobe fglrx
toews@kidlapp:~$ 

```when i went to synaptic and searched fglrx both packages aren't installed..? (fglrx and fglrx-amdcccle)

what is checked off is "xserver-xorg-video-radeon" but it states 

"Note that this is not the same as the ATI-provided, binary-only, 'fglrx'
driver, which provides additional 3D functionality for some newer Radeon
cards, but is not supported."
remove the fglrx you installed manually and install the one from hardware drivers.
I think its
```

sudo /usr/share/ati/fglrx-uninstall.sh

```

---

### Post by adduds on 2011-02-28
sudo apt-get remove --purge fglrx	

restarted comp and lspci still shows 

```

01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 035d
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at dc400000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at dc440000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: fglrx, radeon

```

with how my lspci is now i installed the fglrx driver through jockey when i rebooted it brought me to a tty1 terminal""""
re-booted again into recovery mode lspci -v states

> 01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 035d
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at dc400000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at dc440000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon


toews@kidlapp:~$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

and my xorg.conf reads:
> # NOXORGCONFEXISTED: No X.org configuration file existed when this backup was created.

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection



---

### Post by adduds on 2011-02-28
so basically what i ended up doing or did was go into my bios and set graphics to discrete rather than switchable...

counter strike source still won't load GRRRRRRRRRRRRR :@

---

### Post by adduds on 2011-03-03
instead of going back and forth between discrete and switchable in my bios before i use win7 or linux

is there anyway i can decide or switch my graphics on and off in ubuntu so i don't always have to reboot and do it in bios prior to using ubuntu??

---

