---
title: "any distro using gnome shell?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-23
i was looking for any debian or ubuntu based distro that uses gnome shell as default. is there any??

---

### Post by ubudog on 2010-08-23
I don't know of any, but can't you just install it in Ubuntu?

---

### Post by fremantle on 2010-08-23
nah i dont wana.

---

### Post by Shutter4U on 2010-08-26
Gnome-shell won't be officially added to Gnome until Gnome 3 comes out, which seems to be around March 2011 (in time to be in Ubuntu 11.04 - maybe?). Not sure if it'll be the default or just an option even then.

Until then you have to either use the ricotz repository or the source code method (jhbuild) to install it.

Once installed, if you want gnome to start with gnome-shell instead of the normal gnome panels, you can add a command to the Startup Applications in the System/Preferences menu.

---

### Post by ubudog on 2010-08-26
> **Shutter4U said:**
> Gnome-shell won't be officially added to Gnome until Gnome 3 comes out, which seems to be around March 2011 (in time to be in Ubuntu 11.04 - maybe?). Not sure if it'll be the default or just an option even then.

Until then you have to either use the ricotz repository or the source code method (jhbuild) to install it.

Once installed, if you want gnome to start with gnome-shell instead of the normal gnome panels, you can add a command to the Startup Applications in the System/Preferences menu.

Yeah, that would be kinda cool.

---

### Post by snowpine on 2010-08-26
Gnome Shell hasn't been released yet, so no distro that I know of uses it by default.

There is a "preview" of Gnome Shell in the latest OpenSUSE and also in the Alpha of Fedora 14. Probably Ubuntu 10.10 Maverick will have a preview as well. :)

---

### Post by ubudog on 2010-08-26
Maybe.

---

### Post by Redsandro on 2011-05-09
What about now?

Fedora 15 is gonna feature Gnome 3. Ubuntu and Mint are not.
Who else is?

---

### Post by compmodder26 on 2011-05-09
Ubuntu 11.10 will use Gnome 3 with Unity as the default shell.  You should be able to to install gnome shell through the repositories should you want to.

As for now, the only two distros I know of using Gnome 3/Gnome Shell are Fedora and OpenSuse

---

### Post by DarwinSurvivor on 2011-05-14
If anyone is feeling adventurous, archlinux has gnome3 in it's repositories.

---

### Post by Redsandro on 2011-05-14
> **DarwinSurvivor said:**
> If anyone is feeling adventurous, archlinux has gnome3 in it's repositories.

What was the saying, Archlinux, "lightweight and simple"? ;)

Anyway, good to know.

---

### Post by r-senior on 2011-05-14
> **compmodder26 said:**
> As for now, the only two distros I know of using Gnome 3/Gnome Shell are Fedora and OpenSuse
+1

[http://www.gnome.org/getting-gnome/](http://www.gnome.org/getting-gnome/)

---

### Post by satanselbow on 2011-05-14
There are plenty of possibllities as far as making your own and even a couple of Gnome 3 Ubuntu ISOs knocking about already.

Check this thread for continuing progress :D

[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

I'm working on a minimal install (from the netinstall ISO) that will boot to gnome-shell by default with a fallback option. No Unity involvement at all :D I was also going to keep it pretty minimal - ie with minimal tweaks and app so you have complete freedom of choice as to what goes on your machine - whilst Unity is the source of most of the complaints about Natty some of the software selection changes raise eyebrows as well... Banshee?!... really?

The biggest problems currently are not getting Gnome-shell onto Ubuntu (pretty trivial once you get your head round it) it is packaging it with the available tools (UCK / remastersys) that is proving more of a problem as they are not 100% Natty compliant... or is it the other way round?

---

### Post by cbowman57 on 2011-05-14
You can run Gnome shell in Ubuntu now, there's no reason to switch distros unless you really want to.

---

### Post by Redsandro on 2011-05-14
> **cbowman57 said:**
> You can run Gnome shell in Ubuntu now, there's no reason to switch distros unless you really want to.

Heard advise here and there that Ubuntu is the worst choice to try out the shell, something with buggy crashy and too many code customizations. Not sure, just what they said.

---

### Post by cbowman57 on 2011-05-14
> **Redsandro said:**
> Heard advise here and there that Ubuntu is the worst choice to try out the shell, something with buggy crashy and too many code customizations. Not sure, just what they said.

There are a lot of people looking for a reason to try out or switch distros, and some that are just so Unity-centric they can't accept the fact that Gnome is going to move on despite Ubuntu's decision to leave it behind but bottom line this is still Linux & people will find ways to make it do what they want.  Gnome 3.0 runs great on Ubuntu and is easily as stable as Unity right now. Not to say it's perfect, or there aren't some bugs to be worked out but my system runs 24/7 and hasn't caused me any real grief in the couple months I've been using it.  Gnome shell is also extremely configurable already. 

I've attached an example below.

---

### Post by cbowman57 on 2011-05-14
BTW, if you think people are raising the roof about being forced to Unity here you should check out the Arch forum and see the wailing & gnashing of teeth because Gnome 3.0 has been introduced.  :)

It's kinda funny, when I was in the military we had a saying: "There are only two good assignments, the one you're leaving and the one you're going to."  IOW, the grass is always greener. :D

---

### Post by Redsandro on 2011-05-14
I'm not really sure what you are saying, that average joe dislikes both Unity and Shell, and use it as an excuse to try out Shell in a different distro? Sorry not my native tongue this English thing. ;)

I for one really dislike Unity, but Shell OTOH seems to be compatible with me. Only tried it for short, so I'd like to get that working in Ubuntu.

I am also distro-shopping but it's not because of the Unity thing. I could easily work with Xubuntu, like I've been doing on my older machine anyway. Xfce used to be Gnomes lightweight replacement, but lately not anymore. However I forsee a boost in popularity because Xfce is now going to be Gnomes gnome2-like replacement without 'shell-crap' [SIZE="1"](metaphorically speaking, as I don't agree with it being crap)[/SIZE].

No, I am distro-shopping because Ubuntu is **a)** making increasingly (in my eyes) bad decisions to turn Ubuntu into a Sweet-16-distro.

For example:[list]
[*]Sweet-16-empathy replaces mature pidgin.
[*]Gimp is too mature for sweet-16-audience, removed.
[*]Category-based panels replaced with sweet-16-Unity
[*]Rhytmbox is reaching maturity, quickly replace it with sweet-16-Banshee
[/list]

and **b)** pushing more and more buggy code into *official releases*. The latest beta from Fedora was more stable than RTM of Ubuntu. The amount of bugs is annoying me on my work-computer, even though that one is running 10.04 LTS for funky's sake.

Now I do appreciate Ubuntus top of the wave position in developments, causing me to have my restricted drivers to automatically work, boot up faster than most distro's, stuff like that. So I am in a real tough pickle deciding where to go next.

---

### Post by cbowman57 on 2011-05-14
Sorry about that Redsandro, some things just don't translate very well.

What I was trying to say is that it's funny watching people using other distros complain about Gnome 3.0, like some here complain about Unity. :)

I know what you mean about Unity, I've used it & can make it work but it's just not comfortable.  Gnome 3 + Synapse is fantastic, for me anyway.  I don't like the direction Ubuntu went with the desktop either but I have no influence so I'll make the best of it.  Like you I am also very comfortable with Xfce or LXDE, etc.. but gnome shell really grabbed me, which was a surprise because when I was tinkering with it in beta form I didn't think I would ever like it.  Now they would have to tear it from my cold dead hands. :)  I've used the Suse distro, and Fedora a little bit but decided that the energy spent learning a new distro would be better spent with Gnome 3, and I have not been disappointed.  I am pretty comfortable saying that gnome shell on Ubuntu is every bit as nice & functional as it is on Suse, and probably Fedora or Arch.  A handful of us are really digging deep into it and learning how to make it work for us.  The link to our thread is in my signature.  We do have a live iso with Gnome 3.0 installed that we are sharing in the hope that if people try it on Ubuntu they will agree with us, or at least have given it a fair shot before they go to something else, or force themselves to adapt to Unity.  We just prefer choices rather than being forced into Ubuntu's idea of a one size fits all desktop.

You are welcome to come lurk or participate, or just grab the iso and see what you think of it.

---

### Post by Redsandro on 2011-05-14
Hah, I haven't seen people crying about Gnome Shell yet, au contraire, a lot of people praising it. But you are probably right, I'm not in too much other distro communities. ;)

Thanks, I'll try it out.

---

### Post by cbowman57 on 2011-05-14
Great, I don't normally frequent forums of other distros either but in pursuit of info on gnome shell I seem to end up there. :)

---

### Post by Redsandro on 2011-05-14
Wow it's like you really don't want to Ubuntu users who are unhappy with Unity to leave. :D

---

### Post by cbowman57 on 2011-05-14
> **Redsandro said:**
> Wow it's like you really don't want to Ubuntu users who are unhappy with Unity to leave. :D

I suppose it might seem that way but I really don't care, I just got tired of people telling me that I would have to be assimilated into Unity or go somewhere else.  I figured I'd stay & fight.  LOL

---

### Post by Redsandro on 2011-05-14
Yes, well I'm glad. I'm no good fighter so I was about to leave the flagship distro, anything but being assimilated. Looks like now there's a chance I'll join the federation again. ;)

---

### Post by cbowman57 on 2011-05-14
Well it's worth a look just for curiousity & if it seems like something you can work with you can focus on being familiar with just the desktop, instead of figuring out another distro & the shell. Just makes sense to me. :)

---

