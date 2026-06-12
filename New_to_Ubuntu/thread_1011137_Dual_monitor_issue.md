---
title: "Dual monitor issue"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by vckeating on 2008-12-14
Hi all,

I'm hoping that someone might be able to help me out with this.  I'm running 8.10 and would like to span across a laptop and an external monitor with an Intel Corporation 82852/855GM Integrated Graphics Device (rev 02).  I've used the 'Screen Resolution' function to do this, but the problem is that if I select something other than 1024x768 for both, it doesn't seem to work.  

I saw that when I choose the 1024x768 option for both monitors it changes my xorg.conf to:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection
```

This works, but my monitors are not 4:3.  When I tried to manually change it to 16:9 by typing in 2640 768, it didn't work - I get a blank screen where the login should be.  

Any ideas on how I could fix this?

Thanks!

---

