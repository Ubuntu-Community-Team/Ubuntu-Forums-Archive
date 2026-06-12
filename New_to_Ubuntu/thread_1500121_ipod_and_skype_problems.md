---
title: "ipod and skype problems"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by ahindmar on 2010-06-02
Hey there
   
  I have a few problems with my computer and I can’t find a way to fix them.  I am a beginner/intermediate with ubuntu so please dumb down your explanations.  I am running on an Acer Aspire 5100 series from 2007. I have updated ubuntu to the latest settings as of June 2, 2010  
   
  Some details about the computer in case this effects things
  
[LIST]
[*]Processor      / Speed:  
[/LIST]
  
[LIST]
[LIST]
[*]AMD       Turion™ 64 X2 Mobile Technology TL-50 (1.6 GHz, 2x 256 KB L2 cache)       or Turion 64 MK-36 (512 KB L2 cache) featuring:  Dual-core       processing, Simultaneous 32- and 64-bit Windows®-compatible support, AMD       PowerNow!™, AMD HyperTransport™, Enhanced Virus Protection and 3DNow!™       Professional technology
[/LIST]
[/LIST]
  
[LIST]
[*]Core      Logic Chipset:
[/LIST]
  
[LIST]
[LIST]
[*]ATI       Radeon® Xpress 1100
[/LIST]
[/LIST]
  
[LIST]
[*]RAM /      Max RAM:
[/LIST]
  
[LIST]
[LIST]
[*]1 GB       / 4 GB using DDR2 533/667 soDIMM modules
[/LIST]
[/LIST]
  
[LIST]
[*]Video      Subsystem:
[/LIST]
  
[LIST]
[LIST]
[*]ATI       Radeon® Xpress 1100 integrated 3D graphics, with up to 128 MB of       shared system memory
[/LIST]
[/LIST]
  
[LIST]
[*]LCD      Properties:
[/LIST]
  
[LIST]
[LIST]
[*]15.4"       WXGA Acer CrystalBrite™ TFT LCD, 
      1280 x 800 x 16.7 million colors
[/LIST]
[/LIST]
  
[LIST]
[*]Hard      Disk Drive:
[/LIST]
  
[LIST]
[LIST]
[*]40GB       or higher
[/LIST]
[/LIST]
   
  First my skype is not working properly.  I have been able to initiate the test call but my microphone that I plug into the computer is not registering.  Skype has told me to edit my sound settings, which I have but I have not found the right setting.  The rest of my audio works fine in terms of watching videos and listening to music
   
  Second what is the best way to add videos and pictures to the ipod.  What programs can I use to convert the video formats to fit into the ipod format.  Currently my videos are in avi format.  My pictures are jpg
   
  Finally my external hard drive has a hard time registering with my computer.  All other flash drives load properly and on the first try but my 160gb (with about 100 gb used) takes a few plug ins/disconnects in order for it to show up.  How can I make it show up on the first try?

---

### Post by alphacrucis2 on 2010-06-02
> **ahindmar said:**
> Hey there
   
  I have a few problems with my computer and I can’t find a way to fix them.  I am a beginner/intermediate with ubuntu so please dumb down your explanations.  I am running on an Acer Aspire 5100 series from 2007. I have updated ubuntu to the latest settings as of June 2, 2010  
   
  Some details about the computer in case this effects things
  
[LIST]
[*]Processor      / Speed:  
[/LIST]
  
[LIST]
[LIST]
[*]AMD       Turion™ 64 X2 Mobile Technology TL-50 (1.6 GHz, 2x 256 KB L2 cache)       or Turion 64 MK-36 (512 KB L2 cache) featuring:  Dual-core       processing, Simultaneous 32- and 64-bit Windows®-compatible support, AMD       PowerNow!™, AMD HyperTransport™, Enhanced Virus Protection and 3DNow!™       Professional technology
[/LIST]
[/LIST]
  
[LIST]
[*]Core      Logic Chipset:
[/LIST]
  
[LIST]
[LIST]
[*]ATI       Radeon® Xpress 1100
[/LIST]
[/LIST]
  
[LIST]
[*]RAM /      Max RAM:
[/LIST]
  
[LIST]
[LIST]
[*]1 GB       / 4 GB using DDR2 533/667 soDIMM modules
[/LIST]
[/LIST]
  
[LIST]
[*]Video      Subsystem:
[/LIST]
  
[LIST]
[LIST]
[*]ATI       Radeon® Xpress 1100 integrated 3D graphics, with up to 128 MB of       shared system memory
[/LIST]
[/LIST]
  
[LIST]
[*]LCD      Properties:
[/LIST]
  
[LIST]
[LIST]
[*]15.4"       WXGA Acer CrystalBrite™ TFT LCD, 
      1280 x 800 x 16.7 million colors
[/LIST]
[/LIST]
  
[LIST]
[*]Hard      Disk Drive:
[/LIST]
  
[LIST]
[LIST]
[*]40GB       or higher
[/LIST]
[/LIST]
   
  First my skype is not working properly.  I have been able to initiate the test call but my microphone that I plug into the computer is not registering.  Skype has told me to edit my sound settings, which I have but I have not found the right setting.  The rest of my audio works fine in terms of watching videos and listening to music
   


Skype normally uses whatever the default source and sink is set to in the pulseaudio sound server. First thing to do is make sure you have the paman stuff installed:

```
sudo apt-get install paman
```

If you already have paman it will tell you. If not, it will install paman plus some other pulse audio utils. Then you should be able to manually control your sources and sinks.

---

### Post by yamfox on 2010-06-02
for a video converter, do this:

> Go to the software center, and go to Edit>Software Sources in the menu bar. Go to "Other Software". Press add, and paste in this:
```
ppa:stebbins/handbrake-snapshots
```
Then reload, and search for handbrake. Install it, and run it from sound and video. Click on source, find the file you want to convert, then click on the ipod preset in the apple menu on the side, and click start.

JPG pictures should work for the ipod. As far as syncing the ipod, install GTKpod.

---

