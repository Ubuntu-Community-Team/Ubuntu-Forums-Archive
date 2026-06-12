---
title: "firefox 3.5.6 and Thunderbird 3"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-12-20
Hi, I am using Mint 8, 64bit with NVIDIA. I just upgraded to Firefox 3.5.6 using Ubuntuzilla as well as to Thunderbird 3. They all seem to function fine and look good. But, I now have no sound or video in Firefox and Thunderbird does not open links anymore. I was passed a site to fix it that is from mozilla talking about a .js file, but I have no clue what it is talking about and it makes no sense to me. For the Firefox video and sound, I have all the plugins installed, and I even put in the restricted extra and Medibuntu is already installed, yet no video playback.
Thanks

---

### Post by michael37 on 2009-12-21
> **AndyP79 said:**
> Hi, I am using Mint 8, 64bit with NVIDIA. I just upgraded to Firefox 3.5.6 using Ubuntuzilla as well as to Thunderbird 3. They all seem to function fine and look good. But, I now have no sound or video in Firefox and Thunderbird does not open links anymore. I was passed a site to fix it that is from mozilla talking about a .js file, but I have no clue what it is talking about and it makes no sense to me. For the Firefox video and sound, I have all the plugins installed, and I even put in the restricted extra and Medibuntu is already installed, yet no video playback.
Thanks

Ubuntuzilla provides 32-bit builds even on your 64-bit systems.  Either run 64-bit of Firefox and Thunderbird and you won't have these problems.  Or download a real huge bunch of 32-bit libraries to enable video and audio for these 32-bit apps on your system.

The only simple problem is opening links.  [See solution here.]("http://kb.mozillazine.org/Default_browser#Setting_the_browser_that_opens_in_Thunderbird_-_Linux")

===================

Moderators: please move this post to The Ubuntu Forum Community  > Other Community Discussions  > 3rd Party Projects  > Projects > Ubuntuzilla

---

### Post by AndyP79 on 2009-12-21
Well, that makes logical sense. I guess I could just unistall the Ubunutzilla version, and just wait till the release comes in Synap.
Thanks for this info

---

### Post by michael37 on 2009-12-21
Unfortunately, it may take a while for supported 64-bit builds of latest Firefox and especially Thunderbird to show up in repositories.

Glad I could help.

---

### Post by nanotube on 2009-12-21
> **AndyP79 said:**
> Hi, I am using Mint 8, 64bit with NVIDIA. I just upgraded to Firefox 3.5.6 using Ubuntuzilla as well as to Thunderbird 3. They all seem to function fine and look good. But, I now have no sound or video in Firefox and Thunderbird does not open links anymore. I was passed a site to fix it that is from mozilla talking about a .js file, but I have no clue what it is talking about and it makes no sense to me. For the Firefox video and sound, I have all the plugins installed, and I even put in the restricted extra and Medibuntu is already installed, yet no video playback.
Thanks

check to see if your plugins show up in about:plugins
if not, see the ubuntuzilla faq for 64bit users for getting 32bit plugins for the 32bit mozilla builds.

---

