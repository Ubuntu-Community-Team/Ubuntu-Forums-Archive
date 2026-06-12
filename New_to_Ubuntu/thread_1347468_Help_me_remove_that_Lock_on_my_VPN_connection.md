---
title: "Help me remove that Lock on my VPN connection"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by fshawa on 2009-12-06
Hi

i am trying to set up a new VPN connection on Ubuntu, which i don't usually have any problems with. normally everything works fine or i can figure it out with a bit of effort

but for some reason i can't figure this out: when i go to my network connections, and to the tab called VPN connections, it is totally locked. I cannot seem to unlock it. it is entirely shaded and there's a little yellow lock next to VPN. it seems i don't have access, which is puzzling.

not sure why this is or what to do, i've checked all basic settings and i should (as the only user and the admin person) have the authority to remove that security barrier. but i can't.

any ideas? i really need to establish a new VPN connection quite soon, as that's the only way to do resarch at my university library remotely.

thanks very much for your thoughts...

f

---

### Post by alienclone on 2009-12-06
the little yellow lock on the tab next to "VPN" is just the icon for that tab.

if there are no connections listed in the box when you open that tab, then your VPN connection that you previously has is gone for some reason and you may need to set it up again.

if there IS a connection listed in the box when you select it, it should then "un-grey" the options.

---

### Post by putu.sundika on 2009-12-06
> **fshawa said:**
> Hi

i am trying to set up a new VPN connection on Ubuntu, which i don't usually have any problems with. normally everything works fine or i can figure it out with a bit of effort

but for some reason i can't figure this out: when i go to my network connections, and to the tab called VPN connections, it is totally locked. I cannot seem to unlock it. it is entirely shaded and there's a little yellow lock next to VPN. it seems i don't have access, which is puzzling.

not sure why this is or what to do, i've checked all basic settings and i should (as the only user and the admin person) have the authority to remove that security barrier. but i can't.

any ideas? i really need to establish a new VPN connection quite soon, as that's the only way to do resarch at my university library remotely.

thanks very much for your thoughts...

f

sorry if i asked,but have you setup your VPN account through Network Connection ? I'ved locked too before I finish setup my VPN account.

---

### Post by fshawa on 2009-12-09
thanks for your replies!! i am really grateful actually that anyone answered at all

to be honest, i've never had (or needed) a VPN connection in the past - i had just assumed it was like setting up a new wireless/dsl connection (ie. easy and straightforward and obvious through Network Connections). so i guess i was wrong and i have to do something particular - can you tell me what that thing is?
 
When i open Network Connections, there is no option under the VPN tab at all - nothing that asks me if i want to set up a new one, or anything. it is all shaded gray, even the button that says  "Add". there appears to be no option i can select, so i'm not clear how i can add a new VPN connection this way: do i need to go somewhere else to enable that access? if so, where?

thank you so so much for helping me - i really desperately need VPN connection as i will travel for holidays soon but still need to continue doing schoolwork :-(

f

---

### Post by fshawa on 2009-12-09
wait so, if i understood properly, it's not locked it's just not ever been set up: 

So does that mean setting up a new VPN something difficult or something i can do myself (considering i don't like, know how to write computer code or anything)?

:-) thanks

---

### Post by callan79 on 2009-12-09
> **fshawa said:**
> wait so, if i understood properly, it's not locked it's just not ever been set up: 

So does that mean setting up a new VPN something difficult or something i can do myself (considering i don't like, know how to write computer code or anything)?


Hi fshawa,

I think I know what's causing your problem.

Firstly, as allenclone said, the padlock is simply the icon for VPN, it represents a secured/encrypted connection. So don't worry about that.

But if you go to the VPN tab and all the buttons are grey, it usually means you have not got the software installed to run VPN.

So, NetworkManager can handle VPN, but this is handled by plugins. When you install Ubuntu, none of the plugins are installed by default. If you go to Applications >> Ubuntu Software Center, and search for VPN, you should find a few NetworkManager plugins.

For example the one I use is the PPTP Connection Manager. You can install this through Software Center, or from terminal :

```
sudo apt-get install network-manager-pptp
```

You can see a list of the other plugins also via terminal :

```
apt-cache search network-manager
```

Once the plugin(s) is/are installed, log out and back in again, then you can add VPN connections!

Cheers
Callan

---

### Post by fshawa on 2009-12-09
!!!

you were totally right, of course! thanks so so much, that was extremely helpful and now my problem is solved!

amazing!!! thanks again!!

---

