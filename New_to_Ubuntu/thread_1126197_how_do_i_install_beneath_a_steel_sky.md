---
title: "how do i install beneath a steel sky?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by superplasmafist on 2009-04-15
im new to most of linux i cant figure out these things
so how do i download and get the game working?

please help me with this

thanks

---

### Post by Jakey_TheSnake on 2009-04-15
Is it a game designed for windows, or linux? 

Give me a couple of links please.

---

### Post by atomizer on 2009-04-15
Like most linux-software, you don't have to look on the internet and download it.

You can use the synaptic package manager. use search-function in synaptic, mark for install and apply.


ScummVM will be installed automaticly with the package.

---

### Post by .Maleficus. on 2009-04-15
You'll need ScummVM to run it.  I'm not sure if there are packages in the repos (I use Arch) so you can try 'sudo apt-get install scummvm' in the terminal, and if it doesn't work, go [here]("http://www.scummvm.org/downloads.php") and download the correct Ubuntu .deb for your architecture.  On that same page, you'll find downloads for the BaSS floppy or CD images.  Put them in the correct folder for ScummVM and then run the program.

---

### Post by superplasmafist on 2009-04-15
i found out about the game from a thread here "cool apps " something

"Beneath a Steel Sky

This is an old cyberpunk point-and-click adventure game that has been ported (with ScummVM) to Linux. It's completely free, can be downloaded from the repositories, and even comes with speech (that is, every line of dialog in the game is spoken). The graphics are a bit dated, but the storyline is excellent. If you enjoyed games like Monkey Island, King Quest and Quest for Glory, you will love this one.

Ok... I'm done. Your turn!"

thats about all i know. I tried to google for more info on how to install and everything but dont get it at all. theres seem to be no info on this for linux

---

### Post by .Maleficus. on 2009-04-15
> **superplasmafist said:**
> i found out about the game from a thread here "cool apps " something

"Beneath a Steel Sky

This is an old cyberpunk point-and-click adventure game that has been ported (with ScummVM) to Linux. It's completely free, can be downloaded from the repositories, and even comes with speech (that is, every line of dialog in the game is spoken). The graphics are a bit dated, but the storyline is excellent. If you enjoyed games like Monkey Island, King Quest and Quest for Glory, you will love this one.

Ok... I'm done. Your turn!"

thats about all i know. I tried to google for more info on how to install and everything but dont get it at all. theres seem to be no info on this for linux
In that case, open Synaptic Package Manager (System > Administration > Synaptic Package Manager) and use the Search feature to search for either Beneath a Steel Sky or ScummVM.  If you search for BaSS and mark it to install, it should also install ScummVM as a dependency.  Once they have downloaded and installed, all you need to do is run ScummVM and it should list your available games.


Edit:  I just searched on the Ubuntu package website for "beneath" and BaSS was the second thing to come up.  Search for that, click the checkbox and then "Install" and it will install ScummVM along with it.

---

### Post by atomizer on 2009-04-15
or type in a terminal
```

sudo apt-get install beneath-a-steel-sky
```

---

### Post by superplasmafist on 2009-04-15
> **.Maleficus. said:**
> In that case, open Synaptic Package Manager (System > Administration > Synaptic Package Manager) and use the Search feature to search for either Beneath a Steel Sky or ScummVM.  If you search for BaSS and mark it to install, it should also install ScummVM as a dependency.  Once they have downloaded and installed, all you need to do is run ScummVM and it should list your available games.


Edit:  I just searched on the Ubuntu package website for "beneath" and BaSS was the second thing to come up.  Search for that, click the checkbox and then "Install" and it will install ScummVM along with it.

ok. i think im installing it right now using the adept manager.

it will take a while. thanks for all the help so far

---

### Post by superplasmafist on 2009-04-15
well i installed the game and scummvm. but the game isnt in any list when i start the scummvm.

also it says add game. but thats only the home folder in there

what should i do?

---

### Post by CatKiller on 2009-04-15
The beneath-a-steel-sky package creates its own menu entry. It calls itself Beneath A Steel Sky and runs ```
/usr/games/scummvm -p /usr/share/scummvm/beneath-a-steel-sky sky
```

---

