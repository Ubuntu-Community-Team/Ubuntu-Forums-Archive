---
title: "Banshee doesn't play at all"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by pythagoreanmetronome on 2011-06-18
I am running 11.04 32-bit pae kernel and at first Banshee worked fine (for a couple of weeks)...  now Banshee has stopped working entirely.  What I mean by "stopped working entirely" is this:  when I open Banshee it shows all of my music as it is supposed to do but no matter how try to get it to play a song it simply sits there dead.  It will never start playing a song at all.  The Triangular Green Play button is totally dead and unresponsive and the track progress indicator bar never starts advancing.  On the other hand, I can play music from my Music folder with both Rhytmbox and VLC just fine like they work normally.  It is only Banshee which sits there dead.  I thought that maybe this behavior would cease with the next updates so I waited for a few days and got some updates through the update manager but Banshee is still broken and I decided to post here...  I ran banshee from the command line to see what the output says and it indicates something is wrong with gstreamer.  See below.  But I have all of the usual gstreamer plugins installed and as I said above both Rhythmbox and VLC play music files correctly. See end line and you will see what it says about gstreamer object not found...


[Info  15:32:01.584] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, i686) @ 2011-04-18 16:21:33 UTC] 
[Info  15:32:03.330] Updating web proxy from GConf 
[Warn  15:32:03.706] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Gio')   at Banshee.Hardware.Gio.UdevMetadataSource.get_IdMediaDevice () 
[0x00000] in <filename unknown>:0    at Banshee.Hardware.Gio.RawBlockDevice.get_IdMediaPlayer () 
[0x00000] in <filename unknown>:0    at Banshee.Hardware.Gio.RawDevice..ctor (Banshee.Hardware.Gio.Manager manager, Banshee.Hardware.Gio.GioMetadataSource gioMetadata, Banshee.Hardware.Gio.UdevMetadataSource udevMetadata) 
[0x00000] in <filename unknown>:0    at Banshee.Hardware.Gio.RawBlockDevice..ctor (Drive drive, Banshee.Hardware.Gio.Manager manager, Banshee.Hardware.Gio.GioDriveMetadetaSource gioMetadata, Banshee.Hardware.Gio.UdevMetadataSource udevMetadata)  
[0x00000] in <filename unknown>:0    at Banshee.ServiceStack.ServiceManager.DelayedInitialize (IService service) [0x00000] in <filename unknown>:0 

[Warn  15:32:06.072] Service `Banshee.Dap.DapService' not initialized: Object reference not set to an instance of an object 

[Error 15:32:10.372] GStreamer resource error: NotFound

---

### Post by conbot on 2011-06-18
You may need to get the Banshee source and rebuild it entirely. Try to launch it from the terminal. As in:

#banshee
{error code here}

---

### Post by pythagoreanmetronome on 2011-06-18
I don't think anyone on Earth started using Ubuntu because they want to rebuild Banshee from source, so if that truly is the only suggestion, then forget Banshee...  I will stick with Rhythmbox.  In the first post I put the error code...  here it is again... any suggestions?

[Warn  16:29:31.015] Service `Banshee.Dap.DapService' not initialized: Object reference not set to an instance of an object
[Error 16:30:03.888] GStreamer resource error: NotFound

---

### Post by pythagoreanmetronome on 2011-06-18
I am marking this as solved.  As it happens my music folder is in a 2TB LVM storage space I created from consolidating the space from a bunch of hard drives and I originally had it mounted in one folder under media and now that same 2TB LVM storage space is mounted in a different folder.  Strangely enough, Banshee still shows all of the files and images from the coverart and suchlike, but the links to the actual files are dead because the files are not in the folder Banshee thinks they are in anymore, so I had to go to 

Edit > Preferences > Source Specific

and reset the music folder and then rescan the music library.

Sheesh.  That was annoying.  Simple and annoying.

---

### Post by alexwi on 2011-07-29
Hi all,

I had the same problem. 

Running Banshee from the terminal yielded a bunch of errors with some notable mentions of gstreamer, which I was playing with last night in order to get banshee to rip cd's to mp3.

Tried removing and reinstalling banshee, but that didn't change things.

Then I closed banshee, renamed the banshee-1 folder (under /home/<User>/.config to xbanshee-1 (so that the settings wouldn't be lost in case I need them later), restarted banshee and it's behaving now (I had to re-import the music into its library, but that was no biggie because I only had two albums at this point).

Alex 520261

---

### Post by shashanksingh on 2011-07-29
Most of the times the problems I have faced with music players are the mounting issues, music players store a library which becomes inconsistent with time.

---

### Post by freedomAboveAll on 2012-06-06
> **shashanksingh said:**
> Most of the times the problems I have faced with music players are the mounting issues, music players store a library which becomes inconsistent with time.

Thank you for mentioning this.  

Tools > Rescan Music Library 

fixed my similar problem.


(I had a bunch of music I had removed from the machine, but forgot to let Banshee know.)

---

