---
title: "Updates/Downloading Causing Full System Locks"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by cinnamonbuntu on 2008-04-19
Hey guys, I'm having a strange issue with my wireless. I got it working 100% on 7.10 last night, but in the process I made QUITE a mess. Since the configuring was all I had done, I did a clean re-install, and repeated the steps I knew were good/omitted things that I knew not to work. Once again the wireless is working. Unfortunately its only to a degree. When updating through the terminal, or via packet management I get a full system lock up. I can't move my mouse, and an alt+prnt screen+REISUB wouldn't even do the trick. On a wired connection directly to either, router or modem everything's fine. Heres a few specifics about my system/connection in hopes to provide some light into my situation.

Wireless Card: Realtek mfg. RT8185L with a generic driver currently. 

Ubuntu Gutsy 7.10 up to date as of original post time.

The network connections tested were both encrypted and open with no noticeable differences in performance/effect.

No output to log file that I could see after lock up.


Feel free to post if you're experiencing similar issues now or before. Might as well help as many people as possible in one post :D

---

### Post by cinnamonbuntu on 2008-04-19
bump bump bump buuuuuump.

Still having the same issue, thinking about trying a ndiswrapper driver even though its mostly functional. Whats the command to blacklist my old driver?

I did a sudo -e blacklist in my /etc/modprobe.d directory and wrote in the changes, but it says I don't have the permission. Owner is root; figured the sudo would give the permissions, but no go.

---

