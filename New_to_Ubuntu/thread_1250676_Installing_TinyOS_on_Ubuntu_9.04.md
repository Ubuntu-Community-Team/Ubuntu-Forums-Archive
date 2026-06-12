---
title: "Installing TinyOS on Ubuntu 9.04"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by genii90 on 2009-08-26
I am trying to install TinyOS on Ubuntu 9.04. However, I do not see any instruction specific to 9.04. So, I decided to use instructions specific to Hardy. These are steps I took:


[LIST=1]
[*]Go to System -> Administration-> Synaptic Package Manager ( from the Top Panel )
[*]In Synaptic Package Manager go to settings ->repositories.
[*]Take 3rd party Software . Click on Add and copy the following. 
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) hardy main
[*]Click OK and then reload repositories
[*]After reload is done, Search for TinyOS and set install and apply changes.
[/LIST]

 My 1st problem at step 5 on the instruction, TinyOS does not show up in Synaptic.

I had used the instructions [here]("http://docs.tinyos.net/index.php/Installing_TinyOS_2.1#Two-step_install_on_your_host_OS_with_Debian_packages") without any success too.
Thanks.

---

### Post by zvacet on 2009-08-27
As far I can understand last Ubuntu version that supported  that installation was Hardy.Maybe somebody else will know more.

---

### Post by replikanxxl on 2010-01-30
This address for hardy is working for karmic as well. so u can use this address still. Cause theres no address for karmic.all u get would be a 404 error

---

