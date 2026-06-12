---
title: "New System build compatibility."
date: 2011-06-02
forum: New to Ubuntu
---

### Post by blue_opal on 2011-06-02
This will be my first ever system build, on this computer i will be primarily running ubuntu, here is the hardware i am hoping to use:
Motherboard: Asus P8Z68-V PRO
CPU: Intel i5 2500k
Graphics Card: Sapphire 6850 Toxic

My question is; is there are compaitbility issues with ubuntu and this hardware?

What is the support like for the graphics card and can i use multiple monitors with it? 

Also the Motherboard seems to have a built in bluetooth adaptor, will I be able to use it on ubuntu?

Also if i was to run kde would all the eye candy be useable on the graphics card or are there compatibility issues?

Thanks, Many Regards.

---

### Post by seawolf167 on 2011-06-02
You should be good to go.

Here is a link to the [[URL="http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English"]x86_64 & x86 proprietary drivers]("http://sites.amd.com/us/game/downloads/Pages/radeon_xp-64.aspx") [/URL]for your graphics card. You should be able to run all your compiz settings on "high" with no issues. Supported *nix (or WINE) games should be fine. Multiple montiors won't be a problem (especially with the proprietary graphics driver suite)

The motherboard shouldn't be an issue, BIOS will control that for the most part and is system independent. CPU is fine provided it is supported by the motherboard. 

The Bluetooth adapter may be hit-or-miss. See if you can find any reviews or discussion of that particular motherboard regarding *nix issues and compatibility.

---

### Post by blue_opal on 2011-06-02
Thanks for the reply, one more question will i be better of sticking with the Hd 6850 or going with an Nvidia card? which has better support on linux?
Regards

---

### Post by seawolf167 on 2011-06-02
They are both quite well supported on *nix systems now - *especially *new[er] cards. Most people on this forum will recommend the open source driver from System -> Administration -> Hardware Drivers, however IMO the proprietary driver works a little better and gives more options for you to tweak.

tldr; you shouldn't have a problem with any new Nvidia or Radeon cards

---

### Post by blue_opal on 2011-06-02
Ok thanks very much for your time and help.
Regards

---

### Post by wolfen69 on 2011-06-02
I would go with nvidia.

---

### Post by I8NY on 2011-06-02
> **blue_opal said:**
> Thanks for the reply, one more question will i be better of sticking with the Hd 6850 or going with an Nvidia card? which has better support on linux?
Regards
i'm running a XFX 6850 right now and it was just as easy to install and set up as a nvidia.  really it is the features and best value that should determine a video card.  it works great for me but getting a 4850 to work a couple years ago was a problem. (but that was 2 yrs ago)

---

### Post by seawolf167 on 2011-06-02
A couple years ago I definitely would have said go with Nvidia, but ATI has really improved their drivers for *nix to the point that for me I no longer notice any issues with with manufacturers new cards using the proprietary drivers.

I've been using the Catalyst drivers for the past year on two cards running in crossfire mode and really like them so far.

---

### Post by LowSky on 2011-06-02
You can't use unity for multiple monitors. Just saying... only classic will work

---

