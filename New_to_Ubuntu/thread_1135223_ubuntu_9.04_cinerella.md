---
title: "ubuntu 9.04 cinerella"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by escobero on 2009-04-24
migrating my laptop to ubuntu I installed jaunty ...

¿now how to install cinerella?

giving me this:
ed@ed-laptop-hp:~$ sudo apt-get install cinelerra 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: cinelerracv but it is not going to be installed or
                      cinelerrahv but it is not installable
E: Broken packages


¿anyone able to help?

thanks in advance

---

### Post by por100pre1 on 2009-04-24
Cinelerra is not in the Ubuntu repositories. Which Cinelerra package are you trying to install?

---

### Post by por100pre1 on 2009-04-24
I just recreated your problem using the Akirad repository:

[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

The only way to resolve this is to notify the repository administrator:

[http://akiradproject.net/](http://akiradproject.net/)

---

### Post by FlyingAustrian on 2009-04-25
Got the same problem. Somebody already tried to contact the repository admin?
I really would like to see cinelerra working in jaunty!

---

### Post by escobero on 2009-04-27
well will contact cinerella poeple

awaiting their login data

saw a post about the same subject in italian :confused:

could someone read this post (sent one or 2 days ago into the cinerella forum) and explain me what is going on? (german frensh would also do)

thanks in advance

---

### Post by escobero on 2009-04-27
well again me

this is the URL of the post [http://akiradproject.net/node/48](http://akiradproject.net/node/48)

to make it easier (sorry I didn't do it at once) :)

---

### Post by Michiel Wittkampf on 2009-05-15
I think the repository doesn't support ubuntu 9.04 yet. See
[http://akiradproject.net/repository]("http://akiradproject.net/repository")

---

### Post by escobero on 2009-05-28
cinelerra is now avalable for 9.04

found this on:[http://cinelerra.org/getting_cinelerra.php#jaunty](http://cinelerra.org/getting_cinelerra.php#jaunty) but for convinience I just copy paste.

copz paste one of the 2 in a terminal as sudo and then install the version according to your computer ....

hf

9.04 Jaunty Jackalope

    for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
    deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main

        Installation notes:
        - For your convenience you can install a package for detecting your version of Ubuntu, installing akirad repository and keeping it updated.
        Just double click on the link [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and install it with GDebi Package Installer.
        Alternatively, use one of the following terminal commands:
        wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
        or
        echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
        - 4 are the packages available in the akirad repository:

            cinelerracv (all computers)
            cinelerracv-gl (best on computer with opengl2.0 shader)
            cinelerracv-smp (best on multiprocessors computer, it allows also opengl2.0 shader)
            cinelerra-swtc (extra Shape Wipe Transitions)

        - Ubuntu jaunty uses Pulse Audio as Sound driver. Since it comes with a PulseAudio ESD compatibility layer, Cinelerra can be set to work with PulseAudio. Simply open Cinelerra and go to Settings->Preferences->Playback->Audio Driver. Select ESound and set the following parameters:
        Server:
        Port: 7007
        - These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
        - Please, report any package bug to akir4d at gmail dot com

---

