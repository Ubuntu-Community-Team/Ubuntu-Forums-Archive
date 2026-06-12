---
title: "connecting a terminal to serial port"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by chris_tikva on 2009-04-05
Hi,

I was trying to find out how to do this but have been unable to get any info on the web.

What I would like to try is to connect an old laptop via the serial port to a ubuntu system and be able to log in from the far end of a wire. Just like in the old days of unix. I guess I can use a null modem cable and run something like minicom on the laptop but what do I have to do to the ubuntu machine to get it to play ball?

Any pointers or advice would be greatly appreciated.

Chris

---

### Post by cmnorton on 2009-04-07
You need to set up a SLIP connection.

Here's one link,

[http://www.linuxquestions.org/questions/linux-networking-3/configuring-slip-in-ubuntu-716436/?highlight=configuring+SLIP](http://www.linuxquestions.org/questions/linux-networking-3/configuring-slip-in-ubuntu-716436/?highlight=configuring+SLIP)

---

### Post by lloyd_b on 2009-04-07
> **cmnorton said:**
> You need to set up a SLIP connection.

Here's one link,

[http://www.linuxquestions.org/questions/linux-networking-3/configuring-slip-in-ubuntu-716436/?highlight=configuring+SLIP](http://www.linuxquestions.org/questions/linux-networking-3/configuring-slip-in-ubuntu-716436/?highlight=configuring+SLIP)

Er, no.  He's talking about connecting the one machine to the other as if it were a dumb terminal.

Once upon a time, it would have been a simple matter of adding the appropriate "getty" line into the file "/etc/inittab".  But Ubuntu has gotten rid of inittab, in favor of, I think, "upstart", which I have no clue how to configure.

At any rate, all that's required is to get "agetty" running on the associated serial port.  Hopefully someone else will wander by with some info on exactly how to do this...

Did a quick Google - here's a link to what I think is the correct information.  It's for Fedora, but Fedora is using the same Upstart system as Ubuntu, so it *should* be correct: [Serial Console with Upstart]("http://un.codiert.org/2008/11/serial-console-with-upstart-for-fedora-9/")

Lloyd B.

---

### Post by chris_tikva on 2009-04-11
Thanks for that. I've now added a new file to /etc/event.d and it works very well.

Chris

---

