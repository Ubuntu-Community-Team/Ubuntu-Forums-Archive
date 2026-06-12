---
title: "cannot open synaptic packet manager, update manager,ubuntu software centre"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by jaj540 on 2011-02-15
pls help..
I have installed ubuntu tweak in my system and changed my logon picture .after i restart the system i couldnot open ubuntu software centre.. it will show starting ubuntu software centre and then nothing comes.. 
then when i took synaptic update manager it shows a error report that[COLOR=Red] 
"
E: Malformed line 1 in source list /etc/apt/sources.list.d/ubuntu-tweak-stable.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."[/COLOR]

then when i take update manager it shows
[COLOR=Red]

 "An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 1 in source list /etc/apt/sources.list.d/ubuntu-tweak-stable.list (dist parse)'   "[/COLOR]


[COLOR=Black]pls help... i cannot open ubuntu tweak also..[/COLOR]

:cry:

---

### Post by amsterdamharu on 2011-02-15
You could execute the following command:
```
sudo rm /etc/apt/sources.list.d/ubuntu-tweak-stable.*
```Then start update manager, package manager and software center.

You have to add the ubuntu tweak repository again later but that might break it again.

---

### Post by arochester on 2011-02-15
Open /etc/apt/sources.list.d/ubuntu-tweak-stable.list  and copy and paste the result here so we can see it.

To open it, open a Terminal and use the command> gksudo gedit /etc/apt/sources.list.d/ubuntu-tweak-stable.list

---

### Post by jaj540 on 2011-02-15
[@ amsterdamharu :   _THANK U VERY MUCH...._]("http://ubuntuforums.org/member.php?u=898154")


NOW I CAN OPEN update manager, packet manager and update manager:p

i was really worried...thanks again

---

### Post by jaj540 on 2011-02-15
@arochester: my prob is solved...

anyway this is the result 
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) main #Ubuntu Tweak Stable Source


when  gksudo gedit /etc/apt/sources.list.d/ubuntu-tweak-stable.list  is typed in termial


really thanks for helping...... i am really greatful

---

