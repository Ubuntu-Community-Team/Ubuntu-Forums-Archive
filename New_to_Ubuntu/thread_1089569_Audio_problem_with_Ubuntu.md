---
title: "Audio problem with Ubuntu"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2009-03-07
I'm very new to Linux and I have got out of my depth with an audio problem.

I Installed Skype and found that I had no audio, so I followed instructions on:-

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

And now I have no sound control at all i.e. I get "No volume control GStreamer plugins and/or devices found" from the speaker symble at the top.

So it looks like I have lost all audio control.

Doug

---

### Post by dougcumiskey123 on 2009-03-09
I have lost my sound as the speaker icon has a no entry sign on it When I try to open the volume control I get 

" No volume control GStreamer plugins and/or devices found."

 I'm a newbee and hopelessly lost.

---

### Post by zevans on 2009-03-09
Well I can answer that one... 

On most desktops "no entry" sign = volume muted - do you have an option to unmute if you right-click on the speaker?

---

### Post by dougcumiskey123 on 2009-03-09
> **zevans said:**
> Well I can answer that one... 

On most desktops "no entry" sign = volume muted - do you have an option to unmute if you right-click on the speaker?

Yes, and this is what I get,

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I know I have a sound card (laptop) I think I need GStreamer but dont know how.

---

### Post by dougcumiskey123 on 2009-03-09
Have you got any suggestions?

> **dougcumiskey123 said:**
> Yes, and this is what I get,

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I know I have a sound card (laptop) I think I need GStreamer but dont know how.

---

### Post by markbuntu on 2009-03-09
It looks like your sound driver (snd_hda-intel) is not working properly, go here for troubleshooting help.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by dougcumiskey123 on 2009-03-09
> **markbuntu said:**
> It looks like your sound driver (snd_hda-intel) is not working properly, go here for troubleshooting help.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I have been around and around, nothing on is working, as soon as I try something is fails, do you have skype I can change OS and use winxp.

---

### Post by dougcumiskey123 on 2009-03-09
What does this mean.

doug@doug-laptop:~$ "lspci -v | less
> 


At his point the terminal has crashed..

---

### Post by Elfy on 2009-03-09
Can I just add that in the thread you have been posting in you ask

> What does this mean.what you have done is add " to the beginning of the code you ran in the terminal "lspci -v | less

Try running it without and it will work.

---

### Post by LowSky on 2009-03-09
I found this thread by your newer one you made about linux not working for you so I'm here to help

you said you follwed those instructions, but I have no idea on how closly you really did, so we will need to take a look at what you actually did

this should help fix things.. HOPEFULLY, [http://ubuntuforums.org/showpost.php?p=5539687&postcount=331]("http://ubuntuforums.org/showpost.php?p=5539687&postcount=331")
I'll post the commands here just incase the link doesn't work
open a terminal (Applications>Accesories> terminal
enter each command one at a time 
```

sudo soundoff
sudo dpkg -r oss-linux
sudo dpkg-reconfigure linux-sound-base
sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
gksudo gedit /etc/modprobe.d/blacklist
```

The preceding command opens your blacklist file in the text editor. Delete all the lines from "blacklist snd-seq" down to the end of the file (make sure the last line in the file refers to a snd module and was not added by another program).
Restart the PC.
Now, re-install ALSA kernel modules with this script: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
Go to System -> Preferences -> Sounds and select Autodetect or ALSA
Any applications that you configured for OSS should be changed back to ALSA, although they should work with the alsa-oss wrapper.

---

### Post by dougcumiskey123 on 2009-03-10
> **LowSky said:**
> I found this thread by your newer one you made about linux not working for you so I'm here to help

you said you follwed those instructions, but I have no idea on how closly you really did, so we will need to take a look at what you actually did

this should help fix things.. HOPEFULLY, [http://ubuntuforums.org/showpost.php?p=5539687&postcount=331]("http://ubuntuforums.org/showpost.php?p=5539687&postcount=331")
I'll post the commands here just incase the link doesn't work
open a terminal (Applications>Accesories> terminal
enter each command one at a time 
```

sudo soundoff
sudo dpkg -r oss-linux
sudo dpkg-reconfigure linux-sound-base
sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
gksudo gedit /etc/modprobe.d/blacklist
```

The preceding command opens your blacklist file in the text editor. Delete all the lines from "blacklist snd-seq" down to the end of the file (make sure the last line in the file refers to a snd module and was not added by another program).
Restart the PC.
Now, re-install ALSA kernel modules with this script: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
Go to System -> Preferences -> Sounds and select Autodetect or ALSA
Any applications that you configured for OSS should be changed back to ALSA, although they should work with the alsa-oss wrapper.

This is the report from using sudo soundoff.......

doug@doug-laptop:~$ sudo soundoff
[sudo] password for doug: 
sudo: soundoff: command not found
doug@doug-laptop:~$

---

### Post by betrunkenaffe on 2009-03-10
To answer your question you posed in the other forum, it's usually very easy to reinstall Linux, even with a dual boot. I just did it 2 times on my desktop (I was testing out Jaunty w/ ext4 and then moved back to Intrepid). I did however break my Windows boot because the bootloader (the little menu when you start up the computer and let's you select Linux vs. Windows) had the wrong information in it. I fixed it by googling "grub windows" and copying the information I found there since it matched my configuration.

Usually I just put the install CD in, boot from it and run the installer, I tell it to only format my ext3 partitions that I made for Linux and then it installs to them. I leave my NTFS (Windows) partition alone because I didn't want to delete the information there. When I reboot 99% of time the bootloader is right (only happened once out of the countless linux installs I've done) and can boot Windows or Linux. The biggest pain I find in a dual boot install is Windows and it's stupid system of stealing the entire HDD if it's unpartitioned.

---

### Post by betrunkenaffe on 2009-03-10
I was curious what the soundoff command was so I tried manpages, google, synaptic and even tried running it...

john@daedalus:~$ sudo soundoff
[sudo] password for john: 
sudo: soundoff: command not found
john@daedalus:~$ 

LOL.

I uninstalled Pulseaudio from my machine, my only suggestion that I don't know if it will work but try installing esound from synaptic..

---

### Post by dougcumiskey123 on 2009-03-10
[QUOTE=betrunkenaffe;6871097] I fixed it by googling "grub windows" and copying the information I found there since it matched my configuration./QUOTE]

I googled "grub windows" and got  (1 - 10 of about 322,000 for grub windows.)

Should I start reading every one?

---

### Post by dougcumiskey123 on 2009-03-10
I uninstalled Pulseaudio from my machine, my only suggestion that I don't know if it will work but try installing esound from synaptic..[/QUOTE]

I seached synaptic and it seems that Esound is unknown.

---

### Post by dougcumiskey123 on 2009-03-10
[QUOTE=betrunkenaffe;6871097

Usually I just put the install CD in, boot from it and run the installer, I tell it to only format my ext3 partitions that I made for Linux and then it installs to them. I leave my NTFS (Windows) partition alone because I didn't want to delete the information there. When I reboot 99% of time the bootloader is right (only happened once out of the countless linux installs I've done) and can boot Windows or Linux. The biggest pain I find in a dual boot install is Windows and it's stupid system of stealing the entire HDD if it's unpartitioned.[/QUOTE]

I do not feel confident enough to follow these instructions, at this moment I simply can't risk loosing my internet contact with a systems crash.

---

### Post by betrunkenaffe on 2009-03-10
Can your machine boot from usb? Do you have a spare usb key? you could try putting the distro on the usb stick and then boot from that, no install needed (all you have to do is download iso that you would burn to a disk and then use the System->Administration->Create a USB Startup Disk utility), you could play with settings with that, save them to the USB and find out if you can get it working without affecting your actual HDD in any way.

It's odd that you couldn't find esound, do you have internet access on the computer? I found it in synaptic (System->Administration->Synaptic Package Manager) when I looked. I didn't find it in Add/Remove Applications.

Also, as per my standard process, I start at the top of the list and go down on the results. It's usually in the top few. I think that one was in top 3.

---

### Post by dougcumiskey123 on 2009-03-10
> **betrunkenaffe said:**
> Can your machine boot from usb? Do you have a spare usb key? you could try putting the distro on the usb stick and then boot from that, no install needed (all you have to do is download iso that you would burn to a disk and then use the System->Administration->Create a USB Startup Disk utility), you could play with settings with that, save them to the USB and find out if you can get it working without affecting your actual HDD in any way.

It's odd that you couldn't find esound, do you have internet access on the computer? I found it in synaptic (System->Administration->Synaptic Package Manager) when I looked. I didn't find it in Add/Remove Applications.

Also, as per my standard process, I start at the top of the list and go down on the results. It's usually in the top few. I think that one was in top 3.

I will get back to you on the (USB Start up) I think I can set the bios to boot the USB but not sure.

On the "Esound" item I made a manual in Synaptic search and it was in the list so I set all the "Esound" files for reinstall and it completed with no problem, now "Esound" is visable in a synaptic search.

---

### Post by dougcumiskey123 on 2009-03-10
I tried to make a startup disk for 8.10 amd64 but it failed to bootup when restarted the laptop, Now I know that the startup disk that I made for 8.10 386i worked fine so I made another one for that distro, but it failed to complete at the writing stage with the error report:--

The installation failed.  Please see ~/.usb-creator.log for more details.

And on doing this I got:--

doug@doug-laptop:~$ ~/.usb
bash: /home/doug/.usb: No such file or directory
doug@doug-laptop:~$ 

The hole just keeps getting bigger...

---

### Post by betrunkenaffe on 2009-03-10
> **dougcumiskey123 said:**
> I tried to make a startup disk for 8.10 amd64 but it failed to bootup when restarted the laptop, Now I know that the startup disk that I made for 8.10 386i worked fine so I made another one for that distro, but it failed to complete at the writing stage with the error report:--

The installation failed.  Please see ~/.usb-creator.log for more details.

And on doing this I got:--

doug@doug-laptop:~$ ~/.usb
bash: /home/doug/.usb: No such file or directory
doug@doug-laptop:~$ 

The hole just keeps getting bigger...

I have gotten the same error with 64 bit Ubuntu, not sure why. there should be a file called .usb-creator.log in your /home/doug/ directory. Try typing this into your terminal

```
gedit /home/doug/.usb-creator.log
```

and see what happens.I'd suggest if the usb maker failed, boot the Windows, reformat the USB (should be back to it's full size) and then go back in Linux again. I suggest it like this because it's easier than trying to learn to reformat it in Linux when you are already having problems, I don't want to increase your frustration level :) Then try making it again. I'm not 100% sure why but I've had it fail a few times trying to make USBs and then had 100% success time after time. I don't know what the deciding factor is that causes it to start failing again (same file too). I agree, this aspect is annoying but at the same time, it's not THAT bad..

On the sound thing, can you access sound panel again?

---

### Post by dougcumiskey123 on 2009-03-11
> **betrunkenaffe said:**
> I have gotten the same error with 64 bit Ubuntu, not sure why. there should be a file called .usb-creator.log in your /home/doug/ directory. Try typing this into your terminal

```
gedit /home/doug/.usb-creator.log
```

and see what happens.I'd suggest if the usb maker failed, boot the Windows, reformat the USB (should be back to it's full size) and then go back in Linux again. I suggest it like this because it's easier than trying to learn to reformat it in Linux when you are already having problems, I don't want to increase your frustration level :) Then try making it again. I'm not 100% sure why but I've had it fail a few times trying to make USBs and then had 100% success time after time. I don't know what the deciding factor is that causes it to start failing again (same file too). I agree, this aspect is annoying but at the same time, it's not THAT bad..

On the sound thing, can you access sound panel again?

Ok, The log produced quite a bit of text, so I have appended it to the bottom of this post it to this post. I looked at attachments and did not find the path. sorry.

I have been reformating between USB writings as I has spotted a hidden partition that Win did not recognize. Might, in this case, the problem be coursed by trying to make 386i start disk with amd64 installed on the HD? but that would not account for the amd64 start disk failure, if I get time today I will repete the work again with more care!

On the sound, The Icon still has no entree sign on it and a double click still produces :---No volume control GStreamer plugins and/or devices found.



Using:-- to get log of startup disk
gedit /home/doug/.usb-creator.log


-- Starting up at 13:09:51 --

-- Starting up at 19:52:44 --
[19:52:44] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3800817664, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[19:52:44] adding: /dev/sdb1
[19:54:17] possibly adding: /org/freedesktop/Hal/devices/volume_empty_cd_r

-- Starting up at 19:57:40 --
[19:57:40] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3800817664, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[19:57:40] adding: /dev/sdb1

-- Starting up at 19:58:34 --
[19:58:34] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3800817664, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[19:58:34] adding: /dev/sdb1

-- Starting up at 20:00:43 --
[20:00:43] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3800817664, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[20:00:43] adding: /dev/sdb1
[20:01:01] possibly adding: /org/freedesktop/Hal/devices/volume_empty_cd_r

-- Starting up at 20:02:08 --
[20:02:09] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3800817664, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[20:02:09] adding: /dev/sdb1

-- Starting up at 20:04:01 --
[20:04:01] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3800817664, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[20:04:01] adding: /dev/sdb1
[20:04:06] prop modified
[20:04:06] device_udi: /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:04:06] num_changes: 2
[20:04:06] change: volume.mount_point
[20:04:06] change: volume.is_mounted
[20:04:06] removing /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:04:06] deleting /dev/sdb1 from the ui
[20:04:06] device removed and none left.  source = False
[20:04:13] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028
[20:04:13] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0
[20:04:14] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0_scsi_host
[20:04:18] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0_scsi_host_0
[20:04:18] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0_scsi_host_0_scsi_device_lun0
[20:04:19] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0_scsi_host_0_scsi_device_lun0_scsi_generic
[20:04:19] possibly adding: /org/freedesktop/Hal/devices/storage_serial_USB_2_0_Flash_Disk_AA04012700045028_0_0
[20:04:19] children: dbus.Array([dbus.String(u'/org/freedesktop/Hal/devices/temp/125')], signature=dbus.Signature('s'))
[20:04:19] no children or children not vfat
[20:04:19] adding: /dev/sdb
[20:04:19] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:04:19] deleting /dev/sdb from the ui
[20:04:19] device removed and none left.  source = False
[20:04:19] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 0, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[20:04:19] adding: /dev/sdb1
[20:04:19] possibly adding: /org/freedesktop/Hal/devices/volume_part2_size_1024
[20:04:19] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_32e642c6_4fd7_4bf6_8359_4fd659fa8277
[20:04:20] prop modified
[20:04:20] device_udi: /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:04:20] num_changes: 2
[20:04:20] change: volume.mount_point
[20:04:20] change: volume.is_mounted
[20:04:20] prop modified
[20:04:20] device_udi: /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:04:20] num_changes: 2
[20:04:20] change: volume.mount_point
[20:04:20] change: volume.is_mounted

-- Starting up at 20:10:26 --
[20:10:26] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3800817664, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[20:10:26] adding: /dev/sdb1
[20:10:36] prop modified
[20:10:36] device_udi: /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:10:36] num_changes: 2
[20:10:36] change: volume.mount_point
[20:10:36] change: volume.is_mounted
[20:10:36] removing /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:10:36] deleting /dev/sdb1 from the ui
[20:10:36] device removed and none left.  source = False

-- Starting up at 20:10:48 --
[20:11:04] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028
[20:11:04] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0
[20:11:05] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0_scsi_host
[20:11:09] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0_scsi_host_0
[20:11:09] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0_scsi_host_0_scsi_device_lun0
[20:11:10] possibly adding: /org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700045028_if0_scsi_host_0_scsi_device_lun0_scsi_generic
[20:11:10] possibly adding: /org/freedesktop/Hal/devices/storage_serial_USB_2_0_Flash_Disk_AA04012700045028_0_0
ERROR:dbus.proxies:Introspect error on :1.1:/org/freedesktop/Hal/devices/temp/135: dbus.exceptions.DBusException: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/temp/135
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/usbcreator/backend.py", line 181, in device_added
    if child.GetProperty('block.is_volume') and child.GetProperty('volume.fstype') == 'vfat':
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
DBusException: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/temp/135
[20:11:10] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:11:10] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 0, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[20:11:10] adding: /dev/sdb1
[20:11:10] possibly adding: /org/freedesktop/Hal/devices/volume_part2_size_1024
[20:11:11] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_32e642c6_4fd7_4bf6_8359_4fd659fa8277
[20:11:11] prop modified
[20:11:11] device_udi: /org/freedesktop/Hal/devices/volume_uuid_EC4D_8128
[20:11:11] num_changes: 2
[20:11:11] change: volume.mount_point
[20:11:11] change: volume.is_mounted

-- Starting up at 20:49:41 --
[20:49:41] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3068010496, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[20:49:41] adding: /dev/sdb1

-- Starting up at 20:53:00 --
[20:53:00] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': 'EC4D-8128', 'label': '', 'free': 3068010496, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_EC4D_8128'}
[20:53:00] adding: /dev/sdb1
[20:53:39] possibly adding: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_amd64
[20:53:39] got a disc: Ubuntu 8.10 amd64
[20:53:43] updating dest_status as part of update_row_state
[20:53:43] updating dest_status as part of update_row_state
[20:53:43] prop modified
[20:53:43] device_udi: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_amd64
[20:53:43] num_changes: 3
[20:53:43] change: volume.mount_point
[20:53:43] change: volume.is_mounted_read_only
[20:53:43] change: volume.is_mounted
[20:54:04] Installing...
[20:54:04] Source CD: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_amd64
[20:54:04] Destination disk: /dev/sdb1
[20:54:04] Persistence size: 128 MB
[20:54:04] Marking partition 1 as active.
[20:54:04] installing the bootloader to /dev/sdb1.
[20:54:08] ['/usr/share/usb-creator/install.py', '-s', u'/media/cdrom0/.', '-t', '/media/disk', '-p', '128']
[20:54:08] possibly adding: /org/freedesktop/Hal/devices/volume_part2_size_1024
[20:54:08] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_32e642c6_4fd7_4bf6_8359_4fd659fa8277
[20:59:25] Install command exited with code: 0

-- Starting up at 21:13:04 --
[21:13:05] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': '744F-0983', 'label': '', 'free': 3800825856, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_744F_0983'}
[21:13:05] adding: /dev/sdb1
[21:13:20] possibly adding: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_amd64
[21:13:20] got a disc: Ubuntu 8.10 amd64
[21:13:22] updating dest_status as part of update_row_state
[21:13:22] updating dest_status as part of update_row_state
[21:13:22] prop modified
[21:13:22] device_udi: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_amd64
[21:13:22] num_changes: 3
[21:13:22] change: volume.mount_point
[21:13:22] change: volume.is_mounted_read_only
[21:13:22] change: volume.is_mounted
[21:13:48] Installing...
[21:13:48] Source CD: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_amd64
[21:13:48] Destination disk: /dev/sdb1
[21:13:48] Persistence size: 128 MB
[21:13:48] Marking partition 1 as active.
[21:13:48] installing the bootloader to /dev/sdb1.
[21:13:49] ['/usr/share/usb-creator/install.py', '-s', u'/media/cdrom0/.', '-t', '/media/disk', '-p', '128']
[21:13:49] possibly adding: /org/freedesktop/Hal/devices/volume_part2_size_1024
[21:13:49] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_32e642c6_4fd7_4bf6_8359_4fd659fa8277
[21:19:04] Install command exited with code: 0

-- Starting up at 21:28:52 --
[21:28:52] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': '744F-0983', 'label': '', 'free': 2933776384, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_744F_0983'}
[21:28:52] adding: /dev/sdb1
[21:29:05] possibly adding: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[21:29:05] got a disc: Ubuntu 8.10 i386
[21:29:09] updating dest_status as part of update_row_state
[21:29:09] updating dest_status as part of update_row_state
[21:29:09] prop modified
[21:29:09] device_udi: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[21:29:09] num_changes: 3
[21:29:09] change: volume.mount_point
[21:29:09] change: volume.is_mounted_read_only
[21:29:09] change: volume.is_mounted
[21:29:42] Installing...
[21:29:42] Source CD: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[21:29:42] Destination disk: /dev/sdb1
[21:29:42] Persistence size: 128 MB
[21:29:42] Marking partition 1 as active.
[21:29:42] installing the bootloader to /dev/sdb1.
[21:29:46] ['/usr/share/usb-creator/install.py', '-s', u'/media/cdrom0/.', '-t', '/media/disk', '-p', '128']
[21:29:46] possibly adding: /org/freedesktop/Hal/devices/volume_part2_size_1024
[21:29:46] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_32e642c6_4fd7_4bf6_8359_4fd659fa8277
[21:31:31] Install command exited with code: 256
[21:31:31] Forcing shutdown of the install process.
[21:31:31] Install failed.

-- Starting up at 21:37:37 --
[21:37:37] new device:
{'capacity': dbus.UInt64(3808272384L), 'uuid': '3808-3300', 'label': '', 'free': 3800825856, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_3808_3300'}
[21:37:37] adding: /dev/sdb1
[21:37:55] possibly adding: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[21:37:55] got a disc: Ubuntu 8.10 i386
[21:37:59] updating dest_status as part of update_row_state
[21:37:59] updating dest_status as part of update_row_state
[21:37:59] prop modified
[21:37:59] device_udi: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[21:37:59] num_changes: 3
[21:37:59] change: volume.mount_point
[21:37:59] change: volume.is_mounted_read_only
[21:37:59] change: volume.is_mounted
[21:38:28] Installing...
[21:38:28] Source CD: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[21:38:28] Destination disk: /dev/sdb1
[21:38:28] Persistence size: 128 MB
[21:38:28] Marking partition 1 as active.
[21:38:28] installing the bootloader to /dev/sdb1.
[21:38:28] ['/usr/share/usb-creator/install.py', '-s', u'/media/cdrom0/.', '-t', '/media/disk', '-p', '128']
[21:38:28] possibly adding: /org/freedesktop/Hal/devices/volume_part2_size_1024
[21:38:28] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_32e642c6_4fd7_4bf6_8359_4fd659fa8277
[21:40:14] Install command exited with code: 256
[21:40:14] Forcing shutdown of the install process.
[21:40:14] Install failed.

---

### Post by betrunkenaffe on 2009-03-11
I definately don't know what the problem with your sound is.. Go into synaptic and try reinstalling Alsa and GStreamer (and all the parts you have marked down as install) for those 2. I'm going to look at those OSS instructions so I can figure out what they did to your system..

I've noticed the Usb boot maker creates a partition for the install. If you have it completely empty and only using a basic FAT16/FAT32 partition, tends to work. So remove any partitions and make it just 1 on the USB key. I'll also look into exit code 256 and see what that even means.

---

### Post by dougcumiskey123 on 2009-03-11
> **betrunkenaffe said:**
> I definately don't know what the problem with your sound is.. Go into synaptic and try reinstalling Alsa and GStreamer (and all the parts you have marked down as install) for those 2. I'm going to look at those OSS instructions so I can figure out what they did to your system..

I've noticed the Usb boot maker creates a partition for the install. If you have it completely empty and only using a basic FAT16/FAT32 partition, tends to work. So remove any partitions and make it just 1 on the USB key. I'll also look into exit code 256 and see what that even means.

Every thing with a name starting alsa*** is installed but not all are marked with the ubuntu icon.
and the same with Gstreamer

I have checked again the download of the ISO and compared with MD5sum it is correct.

I have checked the burnt CD with the download and it is correct.

I have reformated the USB disk on each occasion and tried to build a start disk but it fails to boot on shutdown. the files are present. and this is the same USB that used to have a working disk of 386i on it.
Doug...

---

### Post by betrunkenaffe on 2009-03-12
Okay, I'm looking through these OSS instructions, I want you to run the following command and maybe we can figure out what is happening. Post up the output from the command after it.

```
cat /etc/modprobe.d/blacklist
```


Also try this:

```
sudo dpkg -r oss-linux
```

And run this command and select Alsa from the list (if you haven't done so already)

```
sudo dpkg-reconfigure linux-sound-base
```

Then do these

```
sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
gksudo gedit /etc/modprobe.d/blacklist
```

If you get ANY errors, stop on that command and post up what the output is.

The results from that first command gives me this.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

---

### Post by dougcumiskey123 on 2009-03-12
I'm looking through these OSS instructions, 

doug@doug-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi



doug@doug-laptop:~$ sudo dpkg -r oss-linux
[sudo] password for doug: 
dpkg - warning: ignoring request to remove oss-linux which isn't installed.
doug@doug-laptop:~$ 

sudo dpkg-reconfigure linux-sound-base

#DOUG. At this point I got a popup inviting me to "ok" which I did, on AJSA. In the past the "ok" button was inactive and never worked, but it worked this time.:D

doug@doug-laptop:~$ sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libesd-alsa0 is already the newest version.
alsa-oss is already the newest version.
alsa-base is already the newest version.
libsdl1.2debian-alsa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

doug@doug-laptop:~$ gksudo gedit /etc/modprobe.d/blacklist

#DOUG. At this point the the black list was different to your sample on the bottom line only.


blacklist soundcore# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
blacklist snd-seq
blacklist snd-seq-device
blacklist snd-seq-dummy
blacklist snd-seq-instr
blacklist snd-seq-midi
blacklist snd-seq-midi-emul
blacklist snd-seq-midi-event
blacklist snd-seq-oss
blacklist snd-seq-virmidi
blacklist snd-dummy
blacklist snd-virmidi
blacklist snd-loopback
blacklist snd-ac97-codec
blacklist snd-ad1816a
blacklist snd-ad1816a-lib
blacklist snd-ad1848
blacklist snd-ad1848-lib
blacklist snd-ainstr-fm
blacklist snd-ainstr-gf1
blacklist snd-ainstr-iw
blacklist snd-ainstr-simple
blacklist snd-ak4117
blacklist snd-ak4531-codec
blacklist snd-ak4xxx-adda
blacklist snd-ali5451
blacklist snd-als100
blacklist snd-als300
blacklist snd-als4000
blacklist snd_aoa
blacklist snd_aoa_codec_tas
blacklist snd_aoa_fabric_layout
blacklist snd_aoa_i2sbus
blacklist snd_aoa_soundbus
blacklist snd-armaaci
blacklist snd-asihpi
blacklist snd-atiixp
blacklist snd-atiixp-modem
blacklist snd-au1x00
blacklist snd-au8810
blacklist snd-au8820
blacklist snd-au8830
blacklist snd-azt2320
blacklist snd-azt3328
blacklist snd-bt87x
blacklist snd-ca0106
blacklist snd-cmi8330
blacklist snd-cmipci
blacklist snd-cs4231
blacklist snd-cs4231-lib
blacklist snd-cs4232
blacklist snd-cs4236
blacklist snd-cs4236-lib
blacklist snd-cs4281
blacklist snd-cs46xx
blacklist snd-cs8427
blacklist snd-darla20
blacklist snd-darla24
blacklist snd-dt019x
blacklist snd-echo3g
blacklist snd-emu10k1
blacklist snd-emu10k1-synth
blacklist snd-emu10k1x
blacklist snd-emu8000-synth
blacklist snd-emux-synth
blacklist snd-ens1370
blacklist snd-ens1371
blacklist snd-es1688
blacklist snd-es1688-lib
blacklist snd-es18xx
blacklist snd-es1938
blacklist snd-es1968
blacklist snd-es968
blacklist snd-fm801
blacklist snd-fm801-tea575x
blacklist snd-gina20
blacklist snd-gina24
blacklist snd-gusclassic
blacklist snd-gusextreme
blacklist snd-gus-lib
blacklist snd-gusmax
blacklist snd-gus-synth
blacklist snd-harmony
blacklist snd-hda-intel
blacklist snd-hdsp
blacklist snd-hdspm
blacklist snd-hwdep
blacklist snd-i2c
blacklist snd-ice1712
blacklist snd-ice1724
blacklist snd-ice17xx-ak4xxx
blacklist snd-indigo
blacklist snd-indigodj
blacklist snd-indigoio
blacklist snd-intel8x0
blacklist snd-intel8x0m
blacklist snd-interwave
blacklist snd-interwave-stb
blacklist snd-korg1212
blacklist snd-layla20
blacklist snd-layla24
blacklist snd-maestro3
blacklist snd-mia
blacklist snd-miro
blacklist snd-mixart
blacklist snd-mixer-oss
blacklist snd-mona
blacklist snd-mpu401
blacklist snd-mpu401-uart
blacklist snd-msnd-pinnacle
blacklist snd-mtpav
blacklist snd-mts64
blacklist snd-nm256
blacklist snd-opl3-lib
blacklist snd-opl3sa2
blacklist snd-opl3-synth
blacklist snd-opl4-lib
blacklist snd-opl4-synth
blacklist snd-opti92x-ad1848
blacklist snd-opti92x-cs4231
blacklist snd-opti93x
blacklist snd-page-alloc
blacklist snd-pc98-cs4232
blacklist snd-pcm
blacklist snd-pcm-oss
blacklist snd-pcsp
blacklist snd-pcxhr
blacklist snd-pdaudiocf
blacklist snd-pdplus
blacklist snd-portman2x4
blacklist snd-powermac
blacklist snd-pxa2xx-ac97
blacklist snd-rawmidi
blacklist snd-rme32
blacklist snd-rme96
blacklist snd-rme9652
blacklist snd-rtctimer
blacklist snd-s3c2410
blacklist snd-sa11xx-uda1341
blacklist snd-sb16
blacklist snd-sb16-csp
blacklist snd-sb16-dsp
blacklist snd-sb8
blacklist snd-sb8-dsp
blacklist snd-sbawe
blacklist snd-sb-common
blacklist snd-serialmidi
blacklist snd-serial-u16550
blacklist snd-sgalaxy
blacklist snd-sonicvibes
blacklist snd-sscape
blacklist snd-sun-amd7930
blacklist snd-sun-cs4231
blacklist snd-sun-dbri
blacklist snd-tea575x-tuner
blacklist snd-tea6330t
blacklist snd-timer
blacklist snd-trident
blacklist snd-trident-synth
blacklist snd-usb-audio
blacklist snd-usb-lib
blacklist snd-usb-usx2y
blacklist snd-util-mem
blacklist snd-via82xx
blacklist snd-via82xx-modem
blacklist snd-vx222
blacklist snd-vx-cs
blacklist snd-vx-lib
blacklist snd-vxp440
blacklist snd-vxpocket
blacklist snd-wavefront
blacklist snd-ymfpci
blacklist snd_hda_intel 
blacklist snd_mixer_oss 
blacklist snd_pcm
blacklist snd_timer
blacklist snd_page_alloc
blacklist snd_hwdep
blacklist snd
blacklist soundcore
blacklist snd_hda_intel 
blacklist snd_mixer_oss 
blacklist snd_pcm
blacklist snd_timer
blacklist snd_page_alloc
blacklist snd_hwdep
blacklist snd

doug@doug-laptop:~$ sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libesd-alsa0 is already the newest version.
alsa-oss is already the newest version.
alsa-base is already the newest version.
libsdl1.2debian-alsa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
doug@doug-laptop:~$ gksudo gedit /etc/modprobe.d/blacklist




END of file Doug

---

### Post by betrunkenaffe on 2009-03-12
Little confused, what was output from after all the instructions?

```
cat /etc/modprobe.d/blacklist
```

Does your sound work now or can you still not unmute it?

If all those snd options are in the blacklist, we'll want to remove them, we'll just want the snd_pcsp in the list. We can always add them back in later since we have the list. I'm pretty sure this blacklist is your problem though.

---

### Post by dougcumiskey123 on 2009-03-14
> **betrunkenaffe said:**
> Little confused, what was output from after all the instructions?

```
cat /etc/modprobe.d/blacklist
```

Does your sound work now or can you still not unmute it?

If all those snd options are in the blacklist, we'll want to remove them, we'll just want the snd_pcsp in the list. We can always add them back in later since we have the list. I'm pretty sure this blacklist is your problem though.

I have sent you a PM but I'm not sure if it went ok, you did not get it let me know.

The situation at the moment is that I have reformated and reinstalled and the sound system is working, I am now working on why I can't get my USB disk to bootup with 8.10 amd64 on it.
 I want to use it as a test board for installing skype.

The files are present on the USB and I do reformat the USB before every attempt at installing but it fails to boot every time.

Doug..

---

