---
title: "Oh, Youtube."
date: 2011-03-04
forum: New to Ubuntu
---

### Post by BrandonAElam on 2011-03-04
Hey, hope you're having a good night.
I was stressing over a MBR error on an old Windows desktop this morning, found Ubuntu and fell in love. 
Trouble is: Youtube. 
I've done a couple gazillion searches and can't seem to find the anyone whose problem is the same as mine. I've uninstalled and reinstalled Chromium and the Mozilla Flash thing a dozen times and can't get you tube to work. Occasionally it will play the very first video I go to after an install, but the very next one will show a white space where the video should be, with these weird white diagonal stripes across the screen. It's only Youtube; Hulu and flash games work fine.

I'm sure I'm not the first person to have this issue. Any clues?
(Additional info: I'm running 10.10 on a Compaq where I'm filling less than 2% of total disk capacity.) 

Thanks in advance.

---

### Post by WinterMadness on 2011-03-04
it may be crashing, try opening the terminal and then type firefox
use the browser to goto youtube, wait for it to stop, then copy and paste relevant info here from the terminal. it will help us know if its crashing

---

### Post by BrandonAElam on 2011-03-04
I don't have Firefox installed. I was using Chromium. Is there a terminal prompt for Chromium?

---

### Post by mmsmc on 2011-03-04
try chromium? maybe, doesnt ubuntu come with firefox

---

### Post by BrandonAElam on 2011-03-04
It does. I just dislike Firefox. You tube wasn't working in Firefox either, so I suspected a Flash problem. And 'Chromium' is unfortunately not a prompt.

---

### Post by GWBouge on 2011-03-04
'chromium-browser' probably ... just type 'chrom' in the terminal and hit tab a time or two and see if anything comes up.

---

### Post by Scary Rob on 2011-03-04
I'm having a similar problem, except some videos are coming out black and white and others are red and seem to be a blown-up top left corner of the video. Although, curiously, even on these red blow-up ones the speech-bubble tags seem to be unaffected. This isn't happening with embedded youtube videos on facebook or any other flash video site. This is happening on both Google Chrome and Firefox.

Assuming that the correct command to do the firefox from terminal thing is "sudo firefox" the terminal isn't actually doing anything of interest in response. The terminal asked for my password, loaded firefox and then proceeded to make no response as I played a video that came up red.

I don't know if any of that is even relevant, but I hope it'll help identify the problem if it is.

---

### Post by BrandonAElam on 2011-03-04
You're right GWBouge. This is what the terminal says:

[QUOTE=My Terminal]whatever@Ubuntu:~$ chromium-browser 
[5818:5818:19720079033:ERROR:chrome/browser/extensions/extension_error_reporter.cc(53)] Extension error: Could not load extension from '/home/whatever/.config/chromium/Default/Extensions/aciahcmjmecflokailenpkdchphgkefd/2.1.1_0'. Apps are not enabled.
[5818:5818:19720079194:ERROR:chrome/browser/extensions/extension_error_reporter.cc(53)] Extension error: Could not load extension from '/home/whatever/.config/chromium/Default/Extensions/mcbkbpnkkkipelfledbfocopglifcfmi/2.2_0'. Apps are not enabled.

(exe:5895): Gdk-WARNING **: XID collision, trouble ahead[/QUOTE]

---

