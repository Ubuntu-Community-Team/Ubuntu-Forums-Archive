---
title: "HDMI+Ubuntu=Not working? 7+HDMI=works?!"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-04-26
can anyone help with this? I'm trying to make my laptop to use my HDMI calbe to use my LCD tv to work with it. In 7 i just had to install the nvidia driver and it was done. But in ubuntu i'm having some troubles :/

edit:it's not showing any external display at all in my nvidia settings manager.

---

### Post by steve101101 on 2009-04-26
have you installed and enabled the needed driver?

---

### Post by SunnyRabbiera on 2009-04-26
HDMI does worrk with Linux, I know that, but it depends on the video card I guess

---

### Post by 133794m3r on 2009-04-26
yes, i have installed the Nvidia driver from synaptics as intstructed by another member. But it sill does not show up for me.

---

### Post by Ocxic on 2009-04-26
if your trying to use your onboard HDMI, and also have a video card installed in your system the port won't work, as the BIOS disables it. 

?!? Why does HDMI not work in ubuntu???

---

### Post by 133794m3r on 2009-04-26
well that's what i'd like to know. I have an onboard HDMI port that works wonderfully in Windows 7 one of the few things that are working wonderfully in windows.  For some reason Ubuntu with the Nvidia driver it won't work.

---

### Post by gn2 on 2009-04-26
Have you tried installing and using using the nvidia-settings package?

---

### Post by danroduw06 on 2009-04-26
Thats funny. I logged on to ask this very same question. I have windows Vista and I can connect my laptop to my 32" TV no problem via HDMI cable, but cannot do it with Ubuntu 8.10. All I get is a horizontally scrambled screen. The colors are there, only scrambled. Anyway to fix this?
-Dan

---

### Post by kxmas on 2009-04-26
I spend a lot of time getting HDMI audio working with my Asus M3N78-EM.

Here's what works for me...

1.  Use Alsa 1.0.19.  There are other threads on how to upgrade ALSA, but here's something real quick.  If my instructions don't work, I suggest finding a method that uses built debian packages and module-assistant.  Anything that mentions /usr/local will probably cause you problems later on.  I uploaded the alsa source packages to my ppa, [https://launchpad.net/~kachristmas/+archive/ppa]("https://launchpad.net/~kachristmas/+archive/ppa"), who knows if it will build.  If it does, install all the alsa packages, including alsa-source.  Then run ```
m-a -f --text-mode auto-install alsa-source
```

2.  Reboot.

3.  Use ```
aplay -L
``` to find the name of the HDMI output.  My output looked like 
```
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

4.  Use output from ```
aplay -L
``` to create ```
/etc/asound.conf
```
My two line /etc/asound.conf looks like this:
```
pcm.!default hdmi:NVidia
pcm.iec958 hdmi:NVidia
```

5.  Reboot.

I found this solution by reading the alsa-user mailing list.  This post, [http://article.gmane.org/gmane.linux.alsa.user/32476]("http://article.gmane.org/gmane.linux.alsa.user/32476") , was particularly useful.

---

### Post by 133794m3r on 2009-04-26
well my issue is with the HDMI video and enabling it i foudn a way for ubuntu to recognize the TV but now it keeps spouting out errors like "unable to replace xorg.conf.backup", unable to replace "xorg.conf". And after i tried to do it myself by well manually editing the xorg file. It said the x server had to be restarted. Upon restarting i get this

```
macarthur@:~$ /etc/init.d/gdm restart
 * Stopping GNOME Display Manager...                                     [ OK ] 
 * Starting GNOME Display Manager...                                     [fail]

```

---

### Post by kxmas on 2009-04-26
> **133794m3r said:**
> well my issue is with the HDMI video and enabling it i foudn a way for ubuntu to recognize the TV but now it keeps spouting out errors like "unable to replace xorg.conf.backup", unable to replace "xorg.conf". And after i tried to do it myself by well manually editing the xorg file. It said the x server had to be restarted. Upon restarting i get this

```
macarthur@:~$ /etc/init.d/gdm restart
 * Stopping GNOME Display Manager...                                     [ OK ] 
 * Starting GNOME Display Manager...                                     [fail]

```

Sorry, I was just so happy that I got my problem solved, that I had to share.

Can you revert your xorg.conf file?  That should get gdm/gnome/X running again.  After that, run ```
sudo nvidia-settings
``` from a terminal window.  That should allow nvidia-settings to write to your xorg.conf

---

### Post by 133794m3r on 2009-04-26
still get the same results when i try to revert it. Also on a sidenote is there anyway to change when the fans kick on? In LInux it seems that Nvidia won't kick on till my GPU gets to 105*C but in windows it would kick on at 79*C. I personally don't like playing on a laptop where it's going to burn off my flesh whilst playing. That temperature would be perfectly fine in a Desktop imo but a laptop no way in hell is that acceptable. I do not plan to have a hot laptop simply b/c Nvidia's driver fro linux decided that the temps are different from windows.

---

### Post by kxmas on 2009-04-26
> **133794m3r said:**
> still get the same results when i try to revert it. Also on a sidenote is there anyway to change when the fans kick on? In LInux it seems that Nvidia won't kick on till my GPU gets to 105*C but in windows it would kick on at 79*C. I personally don't like playing on a laptop where it's going to burn off my flesh whilst playing. That temperature would be perfectly fine in a Desktop imo but a laptop no way in hell is that acceptable. I do not plan to have a hot laptop simply b/c Nvidia's driver fro linux decided that the temps are different from windows.

can you post your xorg.conf and the output from running ```
nvidia-settings -q all
``` ?

As for your fan, try taking a look at nvclock / nvclock-gtk.  Both are install through synaptic or by running ```
sudo apt-get install nvclock-gtk nvclock
```

---

### Post by 133794m3r on 2009-04-26
ok nvclock tells me this when i try to change fan speed
```
macarthur@:~$ nvclock -F auto
It seems your card isn't officialy supported in NVClock yet.
The reason can be that your card is too new.
If you want to try it anyhow [DANGEROUS], use the option -f to force the setting(s).
NVClock will then assume your card is a 'normal', it might be dangerous on other cards.
Also please email the author the pci_id of the card for further investigation.
[Get that value using the -i option].
```

and the xorg
```
(nvidia-settings:5280): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

Attributes for Insanity:0.0:

  Attribute 'OperatingSystem' (Insanity:0.0): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2 (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (Insanity:0.0): 180.44 

  Attribute 'NvControlVersion' (Insanity:0.0): 1.17 

  Attribute 'GLXServerVersion' (Insanity:0.0): 1.4 

  Attribute 'GLXClientVersion' (Insanity:0.0): 1.4 

  Attribute 'OpenGLVersion' (Insanity:0.0): 3.0.0 NVIDIA 180.44 

  Attribute 'XRandRVersion' (Insanity:0.0): 1.3 

  Attribute 'XF86VidModeVersion' (Insanity:0.0): 2.2 

  Attribute 'XvVersion' (Insanity:0.0): 2.2 

  Attribute 'TwinView' (Insanity:0.0): 0.
    'TwinView' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'TwinView' is a read-only attribute.
    'TwinView' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (Insanity:0.0): 0x00010000.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (Insanity:0.0): 0x00010000.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'CursorShadow' (Insanity:0.0): 0.
    'CursorShadow' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'CursorShadow' can use the following target types: X Screen.

  Attribute 'CursorShadowAlpha' (Insanity:0.0): 64.
    The valid values for 'CursorShadowAlpha' are in the range 0 - 254
    (inclusive).
    'CursorShadowAlpha' can use the following target types: X Screen.

  Attribute 'CursorShadowRed' (Insanity:0.0): 0.
    The valid values for 'CursorShadowRed' are in the range 0 - 255
    (inclusive).
    'CursorShadowRed' can use the following target types: X Screen.

  Attribute 'CursorShadowGreen' (Insanity:0.0): 0.
    The valid values for 'CursorShadowGreen' are in the range 0 - 255
    (inclusive).
    'CursorShadowGreen' can use the following target types: X Screen.

  Attribute 'CursorShadowBlue' (Insanity:0.0): 0.
    The valid values for 'CursorShadowBlue' are in the range 0 - 255
    (inclusive).
    'CursorShadowBlue' can use the following target types: X Screen.

  Attribute 'CursorShadowXOffset' (Insanity:0.0): 4.
    The valid values for 'CursorShadowXOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowXOffset' can use the following target types: X Screen.

  Attribute 'CursorShadowYOffset' (Insanity:0.0): 2.
    The valid values for 'CursorShadowYOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowYOffset' can use the following target types: X Screen.

  Attribute 'AssociatedDisplays' (Insanity:0.0): 0x00010000.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

  Attribute 'InitialPixmapPlacement' (Insanity:0.0): 2.
    The valid values for 'InitialPixmapPlacement' are in the range 0 - 4
    (inclusive).
    'InitialPixmapPlacement' can use the following target types: X Screen.

  Attribute 'DynamicTwinview' (Insanity:0.0): 1.
    'DynamicTwinview' is an integer attribute.
    'DynamicTwinview' is a read-only attribute.
    'DynamicTwinview' can use the following target types: X Screen.

  Attribute 'MultiGpuDisplayOwner' (Insanity:0.0): 0.
    'MultiGpuDisplayOwner' is an integer attribute.
    'MultiGpuDisplayOwner' is a read-only attribute.
    'MultiGpuDisplayOwner' can use the following target types: X Screen.

  Attribute 'GlyphCache' (Insanity:0.0): 1.
    The valid values for 'GlyphCache' are in the range 0 - 1 (inclusive).
    'GlyphCache' can use the following target types: X Screen.

  Attribute 'NotebookDisplayChangeLidEvent' (Insanity:0.0): 1.
    'NotebookDisplayChangeLidEvent' is an integer attribute.
    'NotebookDisplayChangeLidEvent' can use the following target types: X
    Screen.

  Attribute 'NotebookInternalLCD' (Insanity:0.0): 0x00010000.
    'NotebookInternalLCD' is a bitmask attribute.
    'NotebookInternalLCD' is a read-only attribute.
    'NotebookInternalLCD' can use the following target types: X Screen, GPU.

  Attribute 'Depth30Allowed' (Insanity:0.0): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true) and
    0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (Insanity:0.0): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'PixmapCache' (Insanity:0.0): 1.
    'PixmapCache' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'PixmapCache' can use the following target types: X Screen.

  Attribute 'PixmapCacheRoundSizeKB' (Insanity:0.0): 1024.
    The valid values for 'PixmapCacheRoundSizeKB' are in the range 4 - 1048576
    (inclusive).
    'PixmapCacheRoundSizeKB' can use the following target types: X Screen.

  Attribute 'SyncToVBlank' (Insanity:0.0): 0.
    'SyncToVBlank' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'SyncToVBlank' can use the following target types: X Screen.

  Attribute 'LogAniso' (Insanity:0.0): 0.
    The valid values for 'LogAniso' are in the range 0 - 4 (inclusive).
    'LogAniso' can use the following target types: X Screen.

  Attribute 'FSAA' (Insanity:0.0): 0.
    Valid values for 'FSAA' are: 0, 1, 5, 7, 8, 9, 10 and 12.
    'FSAA' can use the following target types: X Screen.

  Attribute 'TextureSharpen' (Insanity:0.0): 0.
    'TextureSharpen' is a boolean attribute; valid values are: 1 (on/true) and
    0 (off/false).
    'TextureSharpen' can use the following target types: X Screen.

  Attribute 'AllowFlipping' (Insanity:0.0): 1.
    'AllowFlipping' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'AllowFlipping' can use the following target types: X Screen.

  Attribute 'FSAAAppControlled' (Insanity:0.0): 1.
    'FSAAAppControlled' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'FSAAAppControlled' can use the following target types: X Screen.

  Attribute 'LogAnisoAppControlled' (Insanity:0.0): 1.
    'LogAnisoAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'LogAnisoAppControlled' can use the following target types: X Screen.

  Attribute 'OpenGLImageSettings' (Insanity:0.0): 1.
    The valid values for 'OpenGLImageSettings' are in the range 0 - 3
    (inclusive).
    'OpenGLImageSettings' can use the following target types: X Screen.

  Attribute 'FSAAAppEnhanced' (Insanity:0.0): 0.
    'FSAAAppEnhanced' is a boolean attribute; valid values are: 1 (on/true) and
    0 (off/false).
    'FSAAAppEnhanced' can use the following target types: X Screen.

  Attribute 'BusType' (Insanity:0.0): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU.

  Attribute 'VideoRam' (Insanity:0.0): 524288.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (Insanity:0.0): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU.

  Attribute 'GPUCoreTemp' (Insanity:0.0): 50.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (Insanity:0.0): 169,100.
    The valid values for 'GPU2DClockFreqs' are in the ranges 42 - 338, 25 -
    1100 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (Insanity:0.0): 530,799.
    The valid values for 'GPU3DClockFreqs' are in the ranges 132 - 1060, 199 -
    1100 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (Insanity:0.0): 169,100.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (Insanity:0.0): 530,799.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (Insanity:0.0): 530,799.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'BusRate' (Insanity:0.0): 16.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU.

  Attribute 'GPUErrors' (Insanity:0.0): 0.
    'GPUErrors' is an integer attribute.
    'GPUErrors' is a read-only attribute.
    'GPUErrors' can use the following target types: X Screen.

  Attribute 'GPUPowerSource' (Insanity:0.0): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (Insanity:0.0): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfLevel' (Insanity:0.0): 3.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen, GPU.

  Attribute 'GPUAdaptiveClockState' (Insanity:0.0): 1.
    'GPUAdaptiveClockState' is an integer attribute.
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen, GPU.

  Attribute 'GPUPerfModes' (Insanity:0.0): perf=0, nvclock=169, memclock=100 ;
  perf=1, nvclock=275, memclock=300 ; perf=2, nvclock=400, memclock=300 ;
  perf=3, nvclock=530, memclock=799 

  Attribute 'GvoSupported' (Insanity:0.0): 0.
    'GvoSupported' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'GvoSupported' is a read-only attribute.
    'GvoSupported' can use the following target types: X Screen.

  Attribute 'IsGvoDisplay' (Insanity:0.0): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (Insanity:0.0; display device: DFP-0): 0.
    The valid values for 'DigitalVibrance' are in the range 0 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'FrontendResolution' (Insanity:0.0; display device: DFP-0):
  1366,768.
    'FrontendResolution' is a packed integer attribute.
    'FrontendResolution' is a read-only attribute.
    'FrontendResolution' is display device specific.
    'FrontendResolution' can use the following target types: X Screen, GPU.

  Attribute 'BackendResolution' (Insanity:0.0; display device: DFP-0):
  1366,768.
    'BackendResolution' is a packed integer attribute.
    'BackendResolution' is a read-only attribute.
    'BackendResolution' is display device specific.
    'BackendResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelNativeResolution' (Insanity:0.0; display device: DFP-0):
  1366,768.
    'FlatpanelNativeResolution' is a packed integer attribute.
    'FlatpanelNativeResolution' is a read-only attribute.
    'FlatpanelNativeResolution' is display device specific.
    'FlatpanelNativeResolution' can use the following target types: X Screen,
    GPU.

  Attribute 'FlatpanelBestFitResolution' (Insanity:0.0; display device: DFP-0):
  1366,768.
    'FlatpanelBestFitResolution' is a packed integer attribute.
    'FlatpanelBestFitResolution' is a read-only attribute.
    'FlatpanelBestFitResolution' is display device specific.
    'FlatpanelBestFitResolution' can use the following target types: X Screen,
    GPU.

  Attribute 'DFPScalingActive' (Insanity:0.0; display device: DFP-0): 0.
    'DFPScalingActive' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'DFPScalingActive' is a read-only attribute.
    'DFPScalingActive' is display device specific.
    'DFPScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'GPUScaling' (Insanity:0.0; display device: DFP-0): 2,1.
    Valid values for 'GPUScaling' are: [1, 2 and 3], [1 and 2].
    'GPUScaling' is display device specific.
    'GPUScaling' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingActive' (Insanity:0.0; display device: DFP-0): 0.
    'GPUScalingActive' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'GPUScalingActive' is a read-only attribute.
    'GPUScalingActive' is display device specific.
    'GPUScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (Insanity:0.0; display device: DFP-0): 60.05 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (Insanity:0.0; display device: DFP-0): 60.046 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'XVideoTextureBrightness' (Insanity:0.0): 0.
    The valid values for 'XVideoTextureBrightness' are in the range -512 - 511
    (inclusive).
    'XVideoTextureBrightness' can use the following target types: X Screen.

  Attribute 'XVideoTextureContrast' (Insanity:0.0): 4096.
    The valid values for 'XVideoTextureContrast' are in the range 0 - 8191
    (inclusive).
    'XVideoTextureContrast' can use the following target types: X Screen.

  Attribute 'XVideoTextureHue' (Insanity:0.0): 0.
    The valid values for 'XVideoTextureHue' are in the range 0 - 360
    (inclusive).
    'XVideoTextureHue' can use the following target types: X Screen.

  Attribute 'XVideoTextureSaturation' (Insanity:0.0): 4096.
    The valid values for 'XVideoTextureSaturation' are in the range 0 - 8191
    (inclusive).
    'XVideoTextureSaturation' can use the following target types: X Screen.

  Attribute 'XVideoTextureSyncToVBlank' (Insanity:0.0): 1.
    The valid values for 'XVideoTextureSyncToVBlank' are in the range 0 - 1
    (inclusive).
    'XVideoTextureSyncToVBlank' can use the following target types: X Screen.

  Attribute 'XVideoSyncToDisplay' (Insanity:0.0): 0x00010000.
    'XVideoSyncToDisplay' is a bitmask attribute.
    'XVideoSyncToDisplay' can use the following target types: X Screen.

```

---

### Post by kxmas on 2009-04-26
The nvidia-settings is helpful, but doesn't show which values you're using.  I don't see your xorg.conf file in that post.

Can you post /etc/X11/xorg.conf and might as well post the log file that you got when gdm wouldn't start.  It will be /var/log/Xorg.0.log or /var/log/Xorg.0.log.old

Your main problem is that hdmi output doesn't work from laptop?  Which gpu do you have?  lspci -nvv will tell you

---

### Post by 133794m3r on 2009-04-26
> **kxmas said:**
> The nvidia-settings is helpful, but doesn't show which values you're using.  I don't see your xorg.conf file in that post.

Can you post /etc/X11/xorg.conf and might as well post the log file that you got when gdm wouldn't start.  It will be /var/log/Xorg.0.log or /var/log/Xorg.0.log.old

Your main problem is that hdmi output doesn't work from laptop?  Which gpu do you have?  lspci -nvv will tell you

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Tue Mar 24 06:15:32 PST 2009

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "CMO"
	HorizSync       30.0 - 75.0
	VertRefresh     60.0
	Option         "DPMS"
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	VendorName     "Unknown"
	ModelName      "TSB-TV"
	HorizSync       15.0 - 49.0
	VertRefresh     55.0 - 62.0
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	Option         "TwinView" "0"
	Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Screen"
	Identifier     "Screen1"
	Device         "Device1"
	Monitor        "Monitor1"
	DefaultDepth    24
	Option         "TwinView" "0"
	Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load	"glx"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 9800M GS"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Device"
	Identifier     "Device1"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 9800M GS"
	BusID          "PCI:1:0:0"
	Screen          1
EndSection

Section "ServerFlags"
	Option         "Xinerama" "0"
EndSection
```
that's teh xorg.conf


others

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux Insanity 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 26 15:08:40 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation unknown chipset (0x062b) rev 161, Mem @ 0xfc000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Tue Mar 24 06:11:47 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Tue Mar 24 05:51:43 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9800M GS (G94) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.94.3c.00.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9800M GS at PCI:1:0:0:
(--) NVIDIA(0):     CMO (DFP-0)
(--) NVIDIA(0): CMO (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): CMO (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
(--) NVIDIA(0): DPI set to (99, 102); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event10"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
```

old
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux Insanity 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 26 15:05:56 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation unknown chipset (0x062b) rev 161, Mem @ 0xfc000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.12
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT,
	GeForce 6200, GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7300 GT,
	GeForce 7600 GT, GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE,
	GeForce 7300 GT, GeForce Go 7700, GeForce Go 7600,
	GeForce Go 7600 GT, Quadro NVS 300M, GeForce Go 7900 SE,
	Quadro FX 550M, Quadro FX 560, GeForce 7900 GTX, GeForce 7900 GT,
	GeForce 7900 GS, GeForce Go 7900 GS, GeForce Go 7900 GTX,
	Quadro FX 2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500,
	Quadro FX 1500, Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE,
	GeForce 6100, GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX,
	GeForce 8800 GTS, GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600,
	GeForce 8600 GTS, GeForce 8600 GT, GeForce 8600 GT, GeForce 8600 GS,
	GeForce 8400 GS, GeForce 9500M GS, GeForce 8600M GT,
	GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M,
	Quadro FX 570M, Quadro FX 1600M, Quadro FX 570, Quadro FX 1700,
	GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS, GeForce 8300 GS,
	GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, GeForce 9400 GT, Quadro FX 360M, GeForce 9300M G,
	Quadro NVS 290, GeForce GTX 280, GeForce GTX 260,
	GeForce 8800 GTS 512, GeForce 8800 GT, GeForce 9800 GX2,
	GeForce 8800 GS, GeForce 8800M GTS, GeForce 8800M GTX,
	GeForce 8800 GS, GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX,
	GeForce 9800 GTK+, GeForce 9800 GT, GeForce GTS 250, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600 GS, GeForce 9800M GTS,
	GeForce 9700M GTS, GeForce 9800M GTS, GeForce 9500 GT,
	GeForce 9600M GT, GeForce 9600M GS, GeForce 9600M GT,
	GeForce 9500M G, GeForce 9300 GS, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS, Quadro NVS 150M, Quadro NVS 160M
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA Unknown GPU at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0x7f1321f2c000
(--) NV(0): Total video RAM: 512.0 MB
(--) NV(0):       BAR1 size: 256.0 MB
(--) NV(0):   Mapped memory: 256.0 MB
(II) NV(0): Linear framebuffer mapped at 0x7f1311f2c000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) NV(0): Connector map:
(--) NV(0):   Bus 3 -> SOR0 (LVDS)
(--) NV(0):   Bus 0 -> DAC1
(--) NV(0):   Bus 2 -> SOR1
(--) NV(0): Load detection: 497
(II) NV(0): I2C bus "I2C0" initialized.
(II) NV(0): Output VGA1 using monitor section Monitor0
(II) NV(0): I2C bus "I2C2" initialized.
(II) NV(0): Output DVI1 has no monitor section
(II) NV(0): LVDS native size 1366x768
(II) NV(0): Output LVDS has no monitor section
(II) NV(0): I2C bus "I2C3 (LVDS)" initialized.
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0): I2C device "I2C2:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "I2C2:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus 3...
(II) NV(0): I2C device "I2C3 (LVDS):E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "I2C3 (LVDS):ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: CMO  Model: 1558  Serial#: 0
(II) NV(0): Year: 2007  Week: 40
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 35  vert.: 19
(II) NV(0): Gamma: 2.20
(II) NV(0): No DPMS capabilities specified
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
(II) NV(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 75.5 MHz   Image Size:  344 x 193 mm
(II) NV(0): h_active: 1366  h_sync: 1397  h_sync_end 1462 h_blank_end 1560 h_border: 0
(II) NV(0): v_active: 768  v_sync: 772  v_sync_end 784 v_blanking: 806 v_border: 0
(II) NV(0):  N156B3-L02
(II) NV(0):  CMO
(II) NV(0):  N156B3-L02
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff000daf581500000000
(II) NV(0): 	28110103802313780a07f59a574e8726
(II) NV(0): 	1e505400000001010101010101010101
(II) NV(0): 	0101010101017e1d56c2500026301f41
(II) NV(0): 	4c0058c110000018000000fe004e3135
(II) NV(0): 	3642332d4c30320a2020000000fe0043
(II) NV(0): 	4d4f0a202020202020202020000000fe
(II) NV(0): 	004e31353642332d4c30320a2020005d
(II) NV(0): EDID vendor "CMO", prod id 5464
(II) NV(0): Output VGA1 disconnected
(II) NV(0): Output DVI1 disconnected
(II) NV(0): Output LVDS connected
(II) NV(0): Using exact sizes for initial modes
(II) NV(0): Output LVDS using initial mode 1366x768
(--) NV(0): Virtual size is 1366x1366 (pitch 1536)
(**) NV(0):  Driver mode "1366x768": 75.5 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1366x768"x60.0   75.50  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(--) NV(0): 183.99 MB available for offscreen pixmaps
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(II) NV(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NV(0): Setting screen physical size to 344 x 193
(II) config/hal: Adding input device Video Bus
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event10"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus 3...
(II) NV(0):   ... none found
(II) NV(0): EDID vendor "CMO", prod id 5464
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus 3...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: CMO  Model: 1558  Serial#: 0
(II) NV(0): Year: 2007  Week: 40
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 35  vert.: 19
(II) NV(0): Gamma: 2.20
(II) NV(0): No DPMS capabilities specified
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
(II) NV(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 75.5 MHz   Image Size:  344 x 193 mm
(II) NV(0): h_active: 1366  h_sync: 1397  h_sync_end 1462 h_blank_end 1560 h_border: 0
(II) NV(0): v_active: 768  v_sync: 772  v_sync_end 784 v_blanking: 806 v_border: 0
(II) NV(0):  N156B3-L02
(II) NV(0):  CMO
(II) NV(0):  N156B3-L02
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff000daf581500000000
(II) NV(0): 	28110103802313780a07f59a574e8726
(II) NV(0): 	1e505400000001010101010101010101
(II) NV(0): 	0101010101017e1d56c2500026301f41
(II) NV(0): 	4c0058c110000018000000fe004e3135
(II) NV(0): 	3642332d4c30320a2020000000fe0043
(II) NV(0): 	4d4f0a202020202020202020000000fe
(II) NV(0): 	004e31353642332d4c30320a2020005d
(II) NV(0): EDID vendor "CMO", prod id 5464
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1366x768"x0.0   75.50  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
(II) NV(0): EDID vendor "CMO", prod id 5464
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus 3...
(II) NV(0):   ... none found
(II) NV(0): EDID vendor "CMO", prod id 5464
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
 ddxSigGiveUp: Closing log
```


Edit:Update i can get the HDMI to show video haven't tried audio yet. But IF i move my mouse over to the other screen, it WILL freeze my mouse there and not allow me to go back to ubuntu.

---

### Post by kxmas on 2009-04-26
That's a very confusing xorg.conf.  There are two entries for everything.

Try this xorg.conf to get you to a good starting point.
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	   "Default Device"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 9800M GS"
	BusID          "PCI:1:0:0"
	Driver         "nvidia"
	Option         "NoLogo"	"True"
EndSection

```

---

### Post by 133794m3r on 2009-04-27
ok now i can restart the settings in the gdm. But i'm unsure how the dual screen thing will go i'll try it and post my results.

Edit:Nvm i missed the whole "Fail" part of the terminal just kinda looked over it :/

---

### Post by 133794m3r on 2009-04-28
le bump

---

### Post by 133794m3r on 2009-04-29
ok i guess since none can help i'm going to have to reformat and reinstall ubuntu oh yay happy days.

---

### Post by servicetech on 2009-04-29
I've found Ubuntu/myth TV isn't quite ready for prime time w/o lots of manual configuration/use of terminal commands. Windows 7 is the OS of choice for my HTPC due to relatively easy setup. I'd like to see mythbuntu become more "plug and play" in the near future.

---

### Post by tobiz on 2009-05-01
I eventually got Mythbuntu 8.10 with HDMI working. Basically it was done by installing Nvidia driver from the Nvidia package, not by synaptics and rebuilding the alsa driver with options turned on, check out nvidia linux forum for details.  On the way I had analog and spdif audio working from the m/b into my AV amp.  My AV amp can be set to take HDMI AV input and either output audio via the amp or pass through to the TV.  Never had problems with xorg.conf this gets set up from info polled from TV. HDMI with Ubuntu and this m/b does work, and well! I agree MythTV needs to become more Plug & Play and will will work towards that goal. Mythbuntu is my OS of choice for my HTPC and at the moment it's working very well. Getting it to work has been challenging but fun and very educational. If I'd  really wanted easy setup I'd have bought a Home Theatre system and never touched a PC of any flavour.

---

