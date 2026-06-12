---
title: "Samsung N150: Wireless off and Screen Attach"
date: 2014-09-20
forum: Networking &amp; Wireless
---

### Post by asearle on 2014-09-20
Hi Everyone,

I have recently become a very big fan of Lubuntu:  It is simple and fast and, for friends of mine who currently use Windows, the handling is remarkably similar and therefore easy for them to pick up.

Yes, I have installed Lubuntu on several friends' PCs including a number of old netbooks ... which give excellent performance under Lubuntu and therefore gain a new lease of life.

However ...

I have installed on a number of Samsung N150's:  Perfect candidates for Lubuntu and almost everything works except that I find that ...

a. I cannot switch off Wireless Networking:  Even if I switch off in BIOS Wireless still comes up(!)

b. I cannot attach to an external monitor:  The VGA port seems to be disabled (even if I click around on FN and the screen-switch button F4)

Can anyone help me here?  If I could fix these problems then my Lubuntu world would be perfect  :-)

Regards and many thanks,

Alan Searle
Cologne, Germany

---

### Post by kalehrl on 2014-09-21
>  a. I cannot switch off Wireless Networking:  Even if I switch off in BIOS Wireless still comes up(!)
Right click networking icon in the taskbar and deselect wireless.

---

### Post by kostkon on 2014-09-21
> **asearle said:**
> b. I cannot attach to an external monitor:  The VGA port seems to be disabled (even if I click around on FN and the screen-switch button F4)
```
In Lubuntu, multi monitor display settings are not enabled by default. So when you attach another monitor with your laptop for presentation or extended display, nothing will happen. 
```
Taken from [here]("https://help.ubuntu.com/community/Lubuntu/MultiDisplay").

Hope that helps.

---

### Post by asearle on 2014-09-23
This works but the wireless light/indicator is still on so I am not sure whether it really is deactivated.  And the strange thing is that, whatever I set in the BIO (including OFF) the wireless still comes up active.  Very strange.

---

### Post by asearle on 2014-09-23
> **kostkon said:**
> ```
In Lubuntu, multi monitor display settings are not enabled by default. So when you attach another monitor with your laptop for presentation or extended display, nothing will happen. 
```
Taken from [here]("https://help.ubuntu.com/community/Lubuntu/MultiDisplay").

Hope that helps.

Does this mean that I can never use Lubuntu with external monitors?  (i.e. I should use Ubuntu or Kubuntu instead) Or does it just mean that I need to install some extra drivers/components?

Thanks,
Alan

---

### Post by asearle on 2014-09-23
Just one extra thought:  I have installed Lubuntu but if, for example, there is a problem connecting a screen (with Lubuntu) then, would it be possible to install Ubuntu and then work mostly with Lubuntu but, if an extra screen is needed, boot to Ubuntu?

Does anyone know of a HOWTO explaining how this might be done?

Thanks,
Alan

---

### Post by mörgæs on 2014-09-24
Yes, if you have the hard disk space you can setup another distro next to Lubuntu. 

From a live boot open Gparted and shrink the present install, creating unused space. During the following install you select 'something else' and off you go.

...but before this route, did you try Arandr as described in the link above?

---

### Post by asearle on 2014-09-24
Many thanks for the Arandr tip!  That looks promising and I am sure it will sort out my monitor problem.

Regarding wireless settings, I have found a curious thing:  I have installed Lubuntu 14.04 on both a Samsung NC10 and a Samsung N150 (both very similar Netbooks). As far as I can see the installs on the two Netbooks are identical.

On the NC10 I can click the wireless off in Network Manager and the light goes out and my remaining batter power increases.  

However, on the N150, if I deactivate wireless in Network Manager, wireless is no longer available but the light/indicator is still on and there is no gain in remaining battery power.  This makes me think that Network Manager does not switch off physical wireless activity which is a problem because this is a drain on the battery.

Has anyone else noticed this?  Any tips for me?

Many thanks,
Alan Searle

---

### Post by mörgæs on 2014-09-26
Moving to Network to see if anyone here is able to help.

---

### Post by asearle on 2014-09-30
This has really got me stumped.  Has nobody got an idea why the wireless on/off works with an NC10 but not with an N150.

Any tips would be a great help.  If diagnostics are needed, I can post the findings.

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by asearle on 2014-10-11
Hi Everyone,

After many weeks with this problem it simply "went away" with me now able to fully switch off wireless (including the "active" indicator) by disabling wireless in network manager.

I believe/hope that the solution was an Ubuntu update which fixed the problem.  I am very pleased!

But I have a Samsung "Series5" Ultrabook (model: NP535U3C) which has exactly the same problem:  I can disable wireless in network manager and wireless is no longer available but the indicator light stays on and I have no gain in battery life.  This is a pain because I am convinced that, if I could fully switch off wireless, then I would get much longer working-time before needing to charge the battery.

I hope that this message gets picked up and that someone can fix the problem(?)  Or is it me?  Is there something that I can do to fully switch off wireless on this model?

Many thanks for any tips you can give.

Yours,
Alan Searle

---

