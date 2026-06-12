---
title: "Synergy Problem!!! (two Ubuntu Computers)"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2007-10-19
Ok i have two computers. One is dual booted with windows xp and ubuntu and the other is just ubuntu. I installed synergy before on an all xp network and got it working no problem before! Now Synergy is a little harder to configure on ubuntu. I am pretty confident that my error is in my  synergy.conf. 

The Dual Boot Comp is: brian-desktop (synergy server)
The Just Ubuntu is: brian-server (synergy client)

Synergy.conf (brian-desktop)
    section: screens
    brian-desktop:
    brian-server:
    end

    section: aliases
    brian-desktop:
	192.168.1.137
    brian-server:
    	192.168.1.150
    end

    section: links
    brian-server:
    	left = brian-desktop
    brian-desktop:
    	right = brian-server
    end

    section: options
    screenSaverSync = false
    keystroke(f12) = lockCursorToScreen(toggle)
    end 

My question is what do i need to add or subtract to my Synergy server's .conf file and because for now my .conf files are identical on both client and server what might i do to the .conf file on the client?

---

