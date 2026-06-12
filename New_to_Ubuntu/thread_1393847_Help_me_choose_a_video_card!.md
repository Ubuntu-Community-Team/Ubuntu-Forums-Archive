---
title: "Help me choose a video card!"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by doctorbighands on 2010-01-29
I'm debating between purchasing two different laptops. They each have different, but comparable, video cards. I'd like to know which one will work more seamlessly with Ubuntu before I buy.

Laptop 1: ATI Mobility Radeon HD 5730

Laptop 2: nVidia GeForce GT 325M

I know which one I prefer based on pure specs, but it's more important to me not to have to fight with it or have it be buggy when I install Ubuntu.

Any insight you can shed will be very appreciated!

---

### Post by nhasian on 2010-01-29
in the past ati has been a little problematic but recently a lot of work has gone into the linux kernel for ati GPUs and it is a lot better supported in 2.6.32+  Personally i've always used nVidia and i've never had a problem.

---

### Post by audiomick on 2010-01-29
I have read here and there that ATI is improving, but as far as I know, nVidia has a better track record.
Mine haven't given me any trouble.

---

### Post by halitech on 2010-01-29
Personally I've never had a problem with ati cards until 9.04 when xorg made changes. I'm still using an ati card (HD4350) with no problems.

Personally, I would check the card specs against the ati driver site and see if its supported. 

Most will probably say Nvidia but its person opinion.

---

### Post by audiomick on 2010-01-29
[QUOTE=halitech;8746390
Personally, I would check the card specs against the ati driver site and see if its supported. [/QUOTE]

Actually the best advice, and applies to the nVidia one as well.

---

### Post by drzoo2 on 2010-01-29
> **nhasian said:**
> in the past ati has been a little problematic but recently a lot of work has gone into the linux kernel for ati GPUs and it is a lot better supported in 2.6.32+  Personally i've always used nVidia and i've never had a problem.

I second the Nvidia. Always just worked. That said this is a new card and it won't work out of the box (Enabling the restriced driver). You will have to get the Nvidia binary driver. Unfortunaly, I just looked at their released and beta driver and it doesn't support this yet either. In going with Nvidia you will have to wait a few months until NV binary supports this chip.

z

---

### Post by doctorbighands on 2010-01-29
> **halitech said:**
> Personally, I would check the card specs against the ati driver site and see if its supported.

I found this on an Ubuntu docs page: "Radeon HD support is currently limited, but rapidly improving." I don't really know how to check more specifically than that.

[QUOTE=drzoo2]You will have to get the Nvidia binary driver. Unfortunaly, I just looked at their released and beta driver and it doesn't support this yet either. In going with Nvidia you will have to wait a few months until NV binary supports this chip.[/QUOTE]

This tells me I should probably stick to the ATI card. It's the one I prefer anyway, so that works out fine.

---

### Post by halitech on 2010-01-29
that is the opensource drivers. Check here for the ATI driver

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by doctorbighands on 2010-01-29
> **halitech said:**
> that is the opensource drivers. Check here for the ATI driver

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I went to that site, and I can't find a driver for this card for any OS at all! What does THAT mean??

---

### Post by drzoo2 on 2010-01-29
> **doctorbighands said:**
> I went to that site, and I can't find a driver for this card for any OS at all! What does THAT mean??

The thing about Nvidia is it will be available. I would expect in the next beta release. I can't comment on the ATI as I have never used them and am not familiar with there support.

The nice thing about ATI is their driver is open. If you care about such things.

z

btw, here is a link to the linux NV forums were you can find out more info for yourself
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")

And the driver releases...
[http://www.nvnews.net/vbulletin/showthread.php?t=122606]("http://www.nvnews.net/vbulletin/showthread.php?t=122606")

---

### Post by doctorbighands on 2010-01-29
Ok, so, if I'm understanding everyone correctly, the bottom line is as follows:

It doesn't really matter.

I'm gathering that, although nVidia has a better track record, both cards are so new that neither one will work OOTB at the moment, and it's likely that (eventually) I wouldn't really have an issue with either one of them.

Is all that basically right, or am I really confused?

---

### Post by djdarrin91 on 2010-01-29
I would say nvidia,ive used nvidia card on Ubuntu for quite some time with no real issues. Good luck.

---

### Post by halitech on 2010-01-30
> **doctorbighands said:**
> I went to that site, and I can't find a driver for this card for any OS at all! What does THAT mean??

if you looked specifically for 5730, then no it isn't listed. it's under the Radeon 5700 Series

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English)

---

### Post by audiomick on 2010-01-30
> **doctorbighands said:**
> Ok, so, if I'm understanding everyone correctly, the bottom line is as follows:

It doesn't really matter.

I'm gathering that, although nVidia has a better track record, both cards are so new that neither one will work OOTB at the moment, and it's likely that (eventually) I wouldn't really have an issue with either one of them.

Is all that basically right, or am I really confused?

That's basically right.;)

---

### Post by sinbin on 2010-02-14
> **doctorbighands said:**
> I went to that site, and I can't find a driver for this card for any OS at all! What does THAT mean??

I don't believe that the ATI Mobility Radeon™ HD 5730 is supported by AMD yet. Please see the following website: 

[http://www.amd.com/uk/products/notebook/graphics/ati-mobility-hd-5700/Pages/hd-5730-specs.aspx](http://www.amd.com/uk/products/notebook/graphics/ati-mobility-hd-5700/Pages/hd-5730-specs.aspx)

See note 1 which states that driver support is scheduled for release in 2010.

The link on the page for Support and Drivers refers the user to the laptop vendor/manufacturer for drivers.

---

### Post by bgilbert on 2010-02-26
doctorbighands, I'm looking at getting a laptop with the ati card. If you did end up getting one of the laptops, could you please give a quick post with your experience? I'm curious as to how the graphics card worked out for you, it'd also help anyone with searching for similar answers.

Thanks in advance!

---

