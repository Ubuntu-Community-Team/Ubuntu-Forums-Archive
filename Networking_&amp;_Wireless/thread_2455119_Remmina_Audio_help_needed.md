---
title: "Remmina Audio help needed"
date: 2020-12-12
forum: Networking &amp; Wireless
---

### Post by Paul_Alexander on 2020-12-12
I use Ubuntu 18.04 from home. I connect to my office computer via the Cisco AnyConnect VPN client. I then use Remmina to RDP to my computer in my remote office. Everything has worked great all year. I use Microsoft Teams from my RDP session to handle my meetings and such and that works fine. My Office IT (about four months ago) disabled use of the Microsoft Teams Linux client as well as the Teams client from, the web, from a Linux machine. They claim it's a security risk so blocked it. I work for a very large company. So, what I do is run Microsoft Teams from my business iPad in order to get my audio voice out for others to hear me.

Is it possible to purchase a usb microphone to plug into my ubuntu machine? I run Ubuntu locally, on metal hardware, on a desktop PC. And if so, is it possible to configure Remmina to use my local audio so I can communicate with people via Teams (from my microphone on my local machine) while running Teams in the RDP session?

If you don't know, what would you do in my case? I hate having to rely on my ipad to get my voice out over Teams.

-Paul

---

### Post by Paul_Alexander on 2020-12-15
Any suggestions?

---

### Post by TheFu on 2020-12-15
You have a very specific situation that few people posting here would also have. 
That means next to nobody will have done what you seek to accomplish.
Sorry.

Thankfully, I don't have to deal with big company IT any more. But I would stop using Teams until IT solved the issue.

---

### Post by Paul_Alexander on 2020-12-17
Fair enough. We use MS Teams exclusively so my only choice to consolidate into one home PC platform is to switch to a windoze machine which I cannot bring myself to do so, yes, this problem is mostly self induced by having to rely on my iPad for getting my voice audio out. I'll try to get the official verbiage from my IT folks to share here as to 'why' they've blocked O365 (and hence, MS Teams as well) access from a Linux-based client. Stinks, but oh well.

---

### Post by TheFu on 2020-12-17
Or just run Win10 inside a virtual machine and use that.

---

### Post by Paul_Alexander on 2020-12-17
> **TheFu said:**
> Or just run Win10 inside a virtual machine and use that.

I'd have to buy a win10 seat (license), which for Pro (to get RDP support), would be $200 USD, correct?

If I go this route, will the audio from my microphone plugged into my ubuntu metal tower get pushed to the VM's session to which will hold an rdp session with my PC in my business office in my building? That does seem reasonable assuming there is audio configuration, upon startup, at the vm level and at the rdp level. Is there perhaps an ubuntu approved usb microphone that I can buy to improve my reliability with this kind of a setup? Thanks Fu. I do appreciate any suggestions.

---

### Post by TheFu on 2020-12-17
If your ipad connects to Teams, why wouldn't a Windows 10 Home machine connect from your house too? I don't understand?  No need for RDP with video or audio, just simple productivity stuff.  After all, everyone else working from home is using their personal Windows systems, right? I'd bet most are using Win10 Home just fine.

You can try using a VM and if that doesn't work, use a dual-boot setup. I'd be surprised if a VM doesn't work, but that would be dependent on the hypervisor used.

As for software licenses, when I worked for a huge company any MSFT licenses we had at work were available for our home machines too. That was in our enterprise license agreement, so ask IT about that.

If you are going to be on calls with this - use a headset, please.  I have a plantronics USB setup that works.  For better quality audio recordings, I use a small Samson GoMic. It works well, provided I'm not typing at the time.  The Mic clipped to my desk picks up me banging on my IBM 101M ... most microphones get that noise anyway.  If you need a webcam, I know that Logitech C920 and C270 both work well without feedback and do a good job canceling speaker output from microphone inputs. I have a weekly Linux meeting where we all use webcams and about 50% of us use one of those 2 models. The 270 is much less expensive with the same quality audio and video from what I can see.  If you are recording talking heads for upload later, then get the C920 - it does 1080p which matters, but not for live meetings with 4-50 people.

I need to say - I've never touched Win10 and don't plan to, ever. I'm at a place in my career where I don't have to use Microsoft anything, ever.

---

### Post by Paul_Alexander on 2020-12-17
Well I’m glad you’re able to do that but we have limitations. For instance we haven’t been issued laptops yet and our policy requires being on the office network to access bitbucket and Jenkins etc and our dev vms are on our office PC towers. So to run O365 tools we have to be on a supported windoze os. I can’t flip back effectively to a windoze host just to run outlook and teams. I assume those h/w headsets are good options through Linux and I’ll try the windoze vm route from my Linux host at home. Good tip on the windows license.

---

### Post by TheFu on 2020-12-18
> **Paul_Alexander said:**
> Well I’m glad you’re able to do that but we have limitations. For instance we haven’t been issued laptops yet and our policy requires being on the office network to access bitbucket and Jenkins etc and our dev vms are on our office PC towers. So to run O365 tools we have to be on a supported windoze os. I can’t flip back effectively to a windoze host just to run outlook and teams. I assume those h/w headsets are good options through Linux and I’ll try the windoze vm route from my Linux host at home. Good tip on the windows license.

For web-based tools, have you considered telling your web browser to lie about the browser used?  Often, web-app devs block based on the user-agent reported when it really isn't necessary. If Teams is working with OSX, then it doesn't mandate AD for authentication. It is probably just checking the browser agent string.

If you use VMs on your work machine, can you grab those VMs (or export them to OVA) and bring them home? Most hypervisors work with other hypervisor VM file formats. This assumes your home computer is at least as fast as the work ones. Depending on the sensitivity of your projects, this might not be allowed.

Of course, you could always just invest in masks and go into work or get the company to do that.

For some reason, I thought O-355 was a webapp?  Notice I reduced the number to more accurately reflect the true number of available days annually. ;)

I've not tried to passthru my USB headset to any VMs. I don't think that is necessary.  Audio gets passed from the VM to the hostOS automatically, provided there is a virtual sound card provided to the guestOS.  

Plugged in the headset, started a Linux guest (because that is easy for me), had it play an audio file - it did.

Now for the Win7 VM.  Err.... I heard the login sound, but not through the headphones. Seems I didn't tell pulse to grab the sound from that VM, so it went to the connected speakers, not the headset.  My Windows VM isn't for media - at all. It can't play an mp3.  Because it is Win7, it cannot connect to the internet.  Seems I'm stuck and can't test audio on my Win7 VM. Sorry.  

Eureka!  Heard the shutdown audio through the headset when closing the VM down. Seems to work.  I can't speak for any other hypervisor besides KVM+libvirt.  I use SPICE for audio and display channels.  

Anyway, some options for you to consider.

---

### Post by Paul_Alexander on 2020-12-18
Thanks for the tips! Appreciate it. I&#8217;ll put some time into this matter over the weekend. I must run it remotely so rdp to get into my Windows host in my office is the only option. Security and data policies. We&#8217;re on win10 1909 so should be fine. 

My office forbids coming into the bldg. it&#8217;s just beyond nuts.

---

