---
title: "Wine, Garena, &amp; Warcraft, there must be a way"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by TJCIB on 2008-12-12
I want to play Warcraft 3.
I can play it single player no problem through Wine.
I patched WC3 and can host LAN games.

I want to use Garena since all my friends use it.

I tried this:
[http://www.garena.com/forum/viewthread.php?tid=47183&highlight=linux](http://www.garena.com/forum/viewthread.php?tid=47183&highlight=linux)

and this:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13086](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13086)
(this one gave me tons of trouble, the "git" thing didn't ever seem to work.  But I did get wine patched through some other site I can't locate again.)

and nothing has worked.  When I try to to open Garena it thinks for a second then nothing.  It shows up as a Zombie process in the system monitor.

Can someone please help me in a way that I don't need to have a degree in programming to understand.  I don't mind learning, but everything I've read right now is assuming things that I don't know.

I don't mind totally removing Wine and starting from the beginning.

---

### Post by donkyhotay on 2008-12-12
Depending on how entreched your friends are you might try running hamachi instead. I've used it before for LAN gaming over IP and it has a native linux client.

---

### Post by TJCIB on 2008-12-12
Yeah, but we like to get on there and own people from all over the country as a team...

Unless there is some Hamachi-based circle of dota players...

---

### Post by valentinovamsi on 2009-04-26
I'M NOT THE AUTHOR OF THIS MESSAGE, THIS WAS POSTED BY "ICALLBOTSOLO" IN DOTA-ALLSTARS DISCUSSION FORUM.

If you're using an ubuntu variant, you should be able to run all the commands listed in here as I've written them. If you're not running Ubuntu, you might have to dig around looking for the install files from winehq.com instead of using apt-get.

Your best bet is buying cedega and installing via that.

Second best bet is installing wine ("sudo apt-get install wine"), downloading the garena install file (google up garena), and then type "wine /path/to/install.exe". Install as if it were a windows application.

You should now be able to run garena. The command should be something like wine ~/.wine/drive_c/Program\ Files/Garena/garena.exe
(give or take on the path and filename).

You'll need to install WC3. Put WC3 in a cd-rom drive, mount it (or mount a .iso), and type "wine /cdrom/autorun.exe". Install as normal. Unmount the cd-rom drive, eject, put TFT in, mount the cd-rom drive, and type "wine /cdrom/autorun.exe", and then install as normal. Now you have 2 options here. The first method is the harder way, but it's what I did:
Option 1: Get wine to emulate a windows cd-rom drive as /cdrom/. You should be able to do this with the program "winecfg". I'm not sure where the exact options are, but it shouldn't be too hard to find. Now run the following command: "wine ~/.wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl". The -opengl argument is optional, but TFT uses Direct3D by default, which wine usually has a bit of trouble with, whereas OpenGL seems to work a lot better. Attempt to connect to to battle.net, and update to v1.21b. There was a regression bug in wine v0.9.46 that disabled battle.net. I'm not sure if this has been fixed yet or not. If you cannot connect to battle.net, uninstall wine (sudo apt-get remove wine), and then find a legacy version from winehq.com (I'd recommend 0.9.45). After connecting to battle.net and patching, feel free to umount to cd-rom and eject it.

Option 2 is a bit simpler: umount /cdrom/ and eject it. Go to google and type "1.21b TFT patch" Patch war3 (save the file to ~/.wine/drive_c/Program\ Files/Warcraft\ III/, then run "wine ~/.wine/drive_c/Program\ Files/Warcraft\ III/update.exe"). Run TFT (wine ~/.wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl), and attempt to connect to battle.net. If you can connect, congrats, you're done. If you cannot connect, exit TFT, uninstall wine (sudo apt-get remove wine), install a legacy verison of wine, 0.9.45 or earlier, from winehq.com, then attempt to run TFT again and also connecto to battle.net. You should be able to connect.

Now you need to get garena to run TFT. If anyone has any idea on how to do that, that'd be great since I don't know how off the top of my head.


Also, if you're running compiz, then it shouldn't work with OpenGL at the same time. Unfortunately I can't boot to linux right now, but I have some script set up that automatically exits compiz, pushesd, runs, popsd, sets a loop to check every 5 seocnds to see if WC3 is running, and if it's not running, then compiz runs again.

#!/usr/bin/bash
(compiz exit line)
pushd ~/.wine/drive_c/Program\ Files/Warcraft\ III/
wine Frozen\ Throne.exe -opengl
popd
while (WC3 is running. forget the commands)
sleep 5
end
(compiz --start)


Sorry, I haven't run linux in about 3 months, so I forgot some of the commands, but maybe someone else can help improve what I wrote, and also maybe verify that I said everything accurately.

---

