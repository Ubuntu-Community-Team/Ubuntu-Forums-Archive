---
title: "Cannot Install Audacity"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by gryphoninc on 2011-03-05
Hi all

I have just install Ubuntu 10.10 on my pc

So far so good but having headaches installing Audacity.

I Cannot

Went to Software center and tried installing it through there, and it keeps telling me it cannot.

Then tried through the terminal and I get this message:

[B][I]gryphon@gryphon-A7V266-MX:~$ sudo apt-get install audacity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacity : Depends: libflac++6 (>= 1.2.1) but it is not installable
E: Broken packages[/I][/B]

[IMG]http://i21.photobucket.com/albums/b274/rapiertoledana/Workspace1_002.png[/IMG]

Help me please.

This is just the first question I have, I do not want to return to using  Windows but if Ubuntu is going to give me so many headaches I am off,  please help.:confused:

---

### Post by maqtanim on 2011-03-05
First update your system. Run the following command
```
sudo apt-get update
```
you can also update the system from the **System > Administration > Update Manager**

After the update try to install the audacity again.

---

### Post by donkyhotay on 2011-03-05
That should do it, if it doesn't it means something is wrong with your sources and post the results of
```

cat /etc/apt/sources.list

```

---

