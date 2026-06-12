---
title: "Command Line Confusion"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by myrtle001 on 2011-01-02
Hi.

I have used Ubuntu 10.04 for about six months now, so I'm not that new to the Ubuntu, ***but***, I am completely new to using the commands in the terminal. I've been able to avoid the terminal (mostly) by just finding auto-installers, using the Ubuntu Software Center, Synaptic et cetera. Though, I recently started using VBA-M to emulate some of the old Gameboy Advance games I own and used to play. When I was looking for emulators, I wanted to use one that was able to cheat. But, I got completely confused when this is what the readme file said:
> 
CHEAT CODES
===========
Use the --cheat commandline option. Each --cheat XXXX adds one cheat code (in order
of appearance).
. Up to 100 cheat codes are supported.
. Cheat lists are saved in savestates. Cheats in loaded state should override commandline cheats.
. There are no provisions for toggling individual cheats.
. CTRL-E toggles the global 'cheats enabled' option.
. Note that autofire may not work with cheats enabled (at least for some games).

Two formats are available:
PAR:  --cheat '########:########'
CBA:  --cheat '######## ####'

All # are hexadecimal digits. Only uppercase A-F are accepted.

PAR (action replay, also gameshark): only non-encrypted codes work (if it has a master code, it won't work).
CBA (codebreaker): encrypted codes should work


What do they mean? I guess all I need is for someone to translate this into a more noob-friendly version:wink:.

Thanks in advance!:D

---

### Post by waynefoutz on 2011-01-02
You still don't need to use the terminal here. Right click on your main menu, and choose "edit menus." Find the launcher in the list that pops up, high light it and click the "properties" button. put your cheat line at the end of the command line in the launcher. Close it out, your done.

---

### Post by myrtle001 on 2011-01-02
Alright, I'm trying to figure this out.

For reference, this is what I'm trying to do: [http://www.supercheats.com/gameboyadvance/pokemonemeraldcodes2.htm]("http://www.supercheats.com/gameboyadvance/pokemonemeraldcodes2.htm") (Yes, Pokemon Emerald. Curse this stupid game addiction:p)
Then, scroll to the "Warp Codes" part of the page (sorry, couldn't get a direct link).

So, what I want to do is "Warp" to Navel Rock. How would I write this into the command line? How do I put the both (The "first two" and then the two lines for Navel Rock) cheats in at the same time? By the way, I found the [FONT="Courier New"]vbam[/FONT] launcher. I **was** able to do that ;).

Thanks Again! I really appreciate the help!:D

---

