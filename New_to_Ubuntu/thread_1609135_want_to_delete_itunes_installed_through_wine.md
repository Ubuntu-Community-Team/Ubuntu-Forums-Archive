---
title: "want to delete itunes installed through wine"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by gag1087 on 2010-10-30
hello everyone i am new to linux. i have installed itunes through wine. now i have deleted wine from ubuntu software centre but forgot to delete itunes first. could anyone plz tell me how can i delete itunes???? thanx...

---

### Post by skompier on 2010-10-30
Did you try Applications/Wine/Uninstall Wine Software?

---

### Post by Valkyr333 on 2010-11-06
I don't know if the poster of this thread has tried that, but I have.

I'm wanting to remove iTunes and QuickTime from my Ubuntu, seeing as QuickTime is raping the living Hell out of my system whenever I touch it and iTunes just won't open in the first place. I get that "Starting iTunes ... ... ... Fail!" thing, and it's just a liiiiiiittle bit maddening. ^_^

I tried Applications>>Wine>>Uninstall Wine Software, but telling it to remove either offending program leads to the following:

"Are you sure you want to permanently remove (blank)?" (I hit yes)

Then, it looks like it's processing the action but this results in a message, "iTunes/QuickTime have been successfully installed on your computer" and I end up with nothing changed except that I now have two icons, "QuickTime Player" and "QuickTime Player.lnk" on my desktop, and my screen is tweaking out like Serj Tankian on a five-day crack-binge.

I'm also new to Linux/Ubuntu (as you can probably tell), so if I just can't make these windows programs work, I'd be satisfied just getting rid of them altogether and working with what I've got. Is there perhaps a command I can put in the terminal to get rid of the offending programs?

---

### Post by sikander3786 on 2010-11-06
I think all the software installed in wine should be gone by the removal of wine itself (not sure though).

Wine installs all the software in a virtual C: drive inside a hidden .wine directory in your home folder. You can check there.

Go to your home directory. Press Ctrl + H to see hidden files. Search for .wine and open it. It should have a folder named drive_c. Look inside it if it still contains any software you installed and if it is taking up some space, you can safely delete the whole .wine folder.

If .wine is not present in the home directory, you probably remove all the wine associated programs already.

---

