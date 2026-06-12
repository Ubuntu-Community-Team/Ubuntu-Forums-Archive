---
title: "newbie with problems"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by JohnPave on 2009-05-26
ok so I installed ubuntu yesterday, version 8.04 and I was trying to install Banshee, and I figured out the whole key and ppa thing but I still cant install it! it says I have problems with dependencies, ive tried several versions and they say like this:
1) error: wrong architecture "amd64"
2) error: dependency is not satisfiable: libgtk2.0-0


when i tried to do it by synaptic package manager this happened:

could not mark all packages for instalation or upgrade,
the following packages have unresolvable dependencies.
make sure that all required repositories are added and enabled in preferences-
banshee:
depends: libgtk2.0-0(>=2.16.0) but 2.12.9-3ubuntu5 is to be installed
depends: libxrandr2 (>=2:1.2.99.2) but 2:1.2.2-1 is to be installed


.... and so on

what can i do? i also wanted to instal pencil
and it says like this:

error: dependency is not satisfiable: libgcc1

am i doing something wrong?

---

### Post by Bölvaður on 2009-05-26
disable the software sources you added (if you did) and click my link

[click here to install Banshee]("apt:banshee")

report back and tell us if you still have dependency problems 


btw this is very very very poor title, a better one would be "error: dependency is not satisfiable" or "Banshee, dependency is not satisfied"
look at my signature and see how other's have made similar mistakes.. hard to see which one of them had problems with screen resolution, and was solved with installing correct driver :P


from the banchee website:
"Install from the [Banshee Team PPA]("https://edge.launchpad.net/%7Ebanshee-team/+archive")"
Please.. remove what you did then and install banchee normally from either Add/Remove or Synaptic Package manager. We are in a world where the lines between installing new applications and your desktop computer has been blurred. Using their repositories like they suggest doing is only if you want the latest release that hasnt been tested by the ubuntu guys.

---

### Post by oldos2er on 2009-05-26
Check System, Administration, Software Sources to make sure all repositories are enabled.

---

### Post by JohnPave on 2009-05-26
Hey, thanks a lot, i saw what my problem was, i didnt knew that the diferent versions of ubuntu were called intrepid, jaunty, hardy and so on... so i was trying to do intrepid and jaunty insted of hardy! now im reading  the pocket guide... sorry for the inconvenience and from now on i will make better titles lol!

---

