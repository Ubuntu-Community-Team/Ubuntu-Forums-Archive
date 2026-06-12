---
title: "openbox/thermal sensors?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by dzon65 on 2010-05-19
Okay.Since I like openbox a lot,did this minimal 9.10 openbox standalone install (with gnome panels).Weird thing is that in a OB session,the cpu goes way up,the fan's working like crazy and the heat pumps up.Ten minutes of flash,say,youtube or something will make the pc shutdown.Not so in a gnome session.The gnome is setup pretty much the same way.Thunar as file manager and OB as windowmanager.Here,the cpu is far lower and the fan is on vacation.It's as if in a OB session the thermal sensors are disabled.Anyone an idea how to solve this?Btw,not sure if this happens in an earlier version,9.10 minimal has been a p... in the a.. ever since I installed it.

---

### Post by kerry_s on 2010-05-19
that is strange, did you look at the gnome autostart & see if theres anything that does temps, then you could try adding it to your autostart.sh 

check ~/.config/autostart
or
/xdg/autostart

you can open the with a text editor to see the command.

by the way, i'm now using openbox + xfdesktop + xfce4-panel
so i should be able to help you more on the openbox stuff.

---

### Post by dzon65 on 2010-05-19
Hi kerry.Yeah,strange isn't it?Didn't understand it.Just popped in a brand new HD,thought that was causing it,perhaps due to cache issues but I'm telling you,in gnome everthing works like a charm.There's nothing in the autostart even remotely connected to temps.The moment I switch from gnome-session to OB,wham,cpu/fan go way up.really,it's as if the sensors are simply turned off.

---

### Post by dzon65 on 2010-05-19
What could I add to the autostart to prevent it?Took two screenshots,first gnome,second OB.Both without any application open.OB menu doesn't take anything so..

---

### Post by kerry_s on 2010-05-19
> **dzon65 said:**
> What could I add to the autostart to prevent it?Took two screenshots,first gnome,second OB.Both without any application open.OB menu doesn't take anything so..

post your ~/.config/openbox/autostart.sh, may be you got a bad command in there.

---

### Post by dzon65 on 2010-05-19
Here you go:
gnome-volume-control-applet &
gnome-panel &
nitrogen --restore &
netapplet &

---

### Post by warfacegod on 2010-05-19
Have you compared the running processes in the two different sessions watching for something that is obviously using allot more processor time in Openbox than in Gnome?

---

### Post by dzon65 on 2010-05-19
Yes I did.Not much to be seen though,as difference that is.

---

### Post by kerry_s on 2010-05-19
> **dzon65 said:**
> Here you go:
gnome-volume-control-applet &
gnome-panel &
nitrogen --restore &
netapplet &

:lolflag: thats a short list.

mine looks like this:
```

#!/bin/bash

## required for policykit junk ##
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &

## Other ##


## xfce4 stuff ##
xfce4-panel &
thunar --daemon &
xfdesktop &

## gnome stuff ##
nm-applet --sm-disable &

## preferences ##
xset s 0 0 &
xset -dpms &
xset m 0 0 &

## remove ##
rm -f ~/.xsession-errors &
rm -f ~/.recently-used.xbel &

### scripts ###

## restart transmission if it was running ##
if [ -f "$HOME/.config/transmission/lock" ]; then
  transmission -m &
fi


```

---

### Post by dzon65 on 2010-05-19
Yep,but nearly everything works out of the box so.Exept for that damn cpu of course.Got everything backed up and gonna try a reinstall,gotta get this to work normally.
Hey K,could you post a screenie?

---

### Post by warfacegod on 2010-05-19
Why reinstall the entire OS? Can you use Gnome session to reinstall just Openbox?

---

### Post by dzon65 on 2010-05-19
Feel like burning bridges............wouhahaha!!

---

### Post by warfacegod on 2010-05-19
Need gas?

---

### Post by dzon65 on 2010-05-19
Thanks but no thanks.Took it from the beamer,it was wrecked anyway.

---

### Post by warfacegod on 2010-05-19
High octane, that'll burn a bridge nicely.

---

### Post by kerry_s on 2010-05-19
> **dzon65 said:**
> Yep,but nearly everything works out of the box so.Exept for that damn cpu of course.Got everything backed up and gonna try a reinstall,gotta get this to work normally.
Hey K,could you post a screenie?

it's kinda plain, not dark(bad eyes), just enough to work. :)

---

### Post by dzon65 on 2010-05-19
Intrested in a light theme?This one started out with the sodio obt,but changed it to match my gtk.

---

### Post by dzon65 on 2010-05-19
That would be this one.If you want to complete the setup,you'll need the FF extension stylish (that is,if you use FF).If you want,I post the css which will change the FF toolbarbuttons and tabs.

---

### Post by dzon65 on 2010-05-19
Oh,just saw you use chromium.

---

### Post by kerry_s on 2010-05-19
> **dzon65 said:**
> Intrested in a light theme?This one started out with the sodio obt,but changed it to match my gtk.

thanks, but i custom built mine for speed. i used the clearlooks to do the gtkrc for the grey & i did the openbox theme from scratch to match the gtk theme. no images, just short & sweet, very easy to work with if i ever need to change colors.
check this out for a themerc.

```

border.color:			#494949
padding.width:			2
borderWidth:			0
window.handle.width:		0
*.justify:			center
*.bg:				raised gradient vertical
*.button.*.bg:			raised gradient vertical
*.bg.color:			#929292
*.bg.colorTo:			#494949
*.button.*.bg.color:		#929292
*.button.*.bg.colorTo:		#494949
*.inactive.*.bg.color:		#494949
*.inactive.*.bg.colorTo:	#929292
*.text.color:			black
*.active.text.color:		white
*.disabled.text.color:		grey
*.label.text.color:		white
*.inactive.label.text.color:	grey
*.image.color:			white
*.inactive.*.image.color:	grey
*.items.bg.color:		#DCDAD5
*.items.bg.colorTo:		#DCDAD5
*.active.client.color:		#929292
*.inactive.client.color:	#494949


```

---

### Post by dzon65 on 2010-05-20
That's a short rc.That gtk theme I use is clearlooks,it's the only engine I use.I've only got two themes,day/night,same with OB.Try to keep my pc leight.It's fully loaded and takes 2.3Gb.That's openoffice gimp..... included.That's 1% of the HD capacity.
Kerry,I've got a question.How do I add the power preferences applet to my autostart?For now I did this but  that will open up the window of course:gnome-power-preferences & ,not in gnome but in OB.

---

### Post by kerry_s on 2010-05-20
> **dzon65 said:**
> That's a short rc.That gtk theme I use is clearlooks,it's the only engine I use.I've only got two themes,day/night,same with OB.Try to keep my pc leight.It's fully loaded and takes 2.3Gb.That's openoffice gimp..... included.That's 1% of the HD capacity.
Kerry,I've got a question.How do I add the power preferences applet to my autostart?For now I did this but  that will open up the window of course:gnome-power-preferences & ,not in gnome but in OB.

it should be "gnome-power-manager &", you can look in /etc/xdg/autostart folder, just right click them & open with the text editor, look at the "Exec= ".

hey you ever try the cairo-dock?
i been messing with it for about an hour now, not to shabby i might keep it awhile. it was a bit crashy at first, till i learned what it can't do, like making a launcher that starts with "gksudo" instant crash, but using "sudo" it's okay, lucky i got them in sudoers with nopasswd.

still playing with it.

---

### Post by dzon65 on 2010-05-20
Cairo-dock.If only.It's also an option to put my website shortcuts on it.That way I cold avoid using the gnome panel.BUT.It's my graphic card that prevents me from using it.This has been annoying me for some time now.It's a nvidia 6150 (128mb).The damn thing simply doesn't allow me to set advanced visual effects.The only thing I was ever able to do was 3D-flip or carousel or.... (you know,the "simple" effects).Aaaarrgggh,frustrating when you see cubes working on far older rigs.Mind you,those fancy effects never intrested me but cairo-dock doesn't work as well.I can't get rid of the black background.If I want it to work,my only option is to get a decent card.
Oh,btw,I misread something on that first screenshot.Thaught it said secret service storage.:P:lolflag:

---

### Post by kerry_s on 2010-05-20
> **dzon65 said:**
> Cairo-dock.If only.It's also an option to put my website shortcuts on it.That way I cold avoid using the gnome panel.BUT.It's my graphic card that prevents me from using it.This has been annoying me for some time now.It's a nvidia 6150 (128mb).The damn thing simply doesn't allow me to set advanced visual effects.The only thing I was ever able to do was 3D-flip or carousel or.... (you know,the "simple" effects).Aaaarrgggh,frustrating when you see cubes working on far older rigs.Mind you,those fancy effects never intrested me but cairo-dock doesn't work as well.I can't get rid of the black background.If I want it to work,my only option is to get a decent card.
Oh,btw,I misread something on that first screenshot.Thaught it said secret service storage.:P:lolflag:

you don't need compiz, just "xcompmgr" it's like just the settings. anyways it also can do without that & use fake transparency, but that sucked.

so you just need xcompmgr & cairo-dock, in the startup:

xcompmgr -n &
cairo-dock -c &

be warned though, some of the applets is just made to work with gnome stuff, but there's enough that you can do your own commands, so they work, other things like the systray just throws a error. it's got alot of settings & a decent help for the most common junk.

i put the humanity theme & changed the sub window type. starting to get the hang of it.

by the way i'm using the no opengl version, the other 1 just has so much going on, i'm not ready to mess with it yet.

---

### Post by dzon65 on 2010-05-20
Gonna try with xcompmgr but i'm pretty sure tried it before.Didn't work with compiz,that I'm sure.
Openbox,don't you just hate it?...................yeah wright.Got a openbox setup on an old pc (slitaz).Man,don't think human eyes are equiped for that speed (must be 300mb max on the HD and it flies).

---

