---
title: "Install java 32 bit?"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by boy18nj on 2011-05-22
I recently downloaded Ubuntu 11.04. It works awesome. Thanks to all guys who made this possible.
By default system installed openjdk, which is good but it is 64 bit. And some programs do not work because it is 64 bit.

I was struggling to find out the information which says hey this is 32 bit java, you can download it.

I searched thru internet, synaptic all they install 64 bit. But i need 32 bit. i remember in ubuntu 10.04 there used to ia32 bit java, which is no longer available thru synaptic. please guide me here how can i download 32 bit java thru synaptic?

---

### Post by boy18nj on 2011-05-22
I ran this command in terminal-

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner"

ZOOM...now in synaptic I can see ia32 bit java.

I don't know why there is no 32 bit version for openjdk?

---

### Post by beew on 2011-05-22
You can install sun java from the Canonical partners repository, open Synaptic, go to Settings > Repositories > Other Software and make sure the box Partners Of Canonical is checked.

Then install the following packages: sun-java6-plugin and sun-java6-jdk (this will pull in other packages)

After that you still need to make sun-java your default. Open the terminal and run
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by beew on 2011-05-22
> **boy18nj said:**
> I ran this command in terminal-

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner"

ZOOM...now in synaptic I can see ia32 bit java.

I don't know why there is no 32 bit version for openjdk?

I think sun-java is not in the partners repository for Maverick, you can install it from ppas.
For example this one works. [URL="https://launchpad.net/%7Eferramroberto/+archive/java"]https://launchpad.net/~ferramroberto/+archive/java
[/URL]
Add the ppa to your sources list and then install and run update-java-alternatives following my last post.
[B]
EDITED:[/B] Opps you are running 11.04 so why are you downloading Maverick's partner repo? Forget the above and just follow iinstructions from my
last post. Didn't notice you are actually OP (though the ppa also works for Natty and actually has more updated version than from the partners repo)

---

### Post by boy18nj on 2011-05-25
Thank very much for your reply. I was wondering even if my Ubuntu is 32 bit, why it would bother to install 64 bit program without giving any warning?

---

