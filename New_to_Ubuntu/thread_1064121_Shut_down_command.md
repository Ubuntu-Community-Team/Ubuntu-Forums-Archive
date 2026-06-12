---
title: "Shut down command"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by bob brazie on 2009-02-08
I would like to change the command “gnome-session-save –kill” that an icon carries out.

The properties of that icon (above) only lets me log off as one user and on as another. I would like it to shut the computer off and not offer any other options.

Thanks in advance. Bob.

---

### Post by paydaydaddy on 2009-02-08
Shutdown for a single computer:
The most common way of shutting down a single user Linux system is for you as root to issue the command:

    sudo shutdown -h now

You use this when you plan on shutting your computer off at that moment, as opposed to some later time.

You'll see a message like:

    Linux is going for system halt NOW

It will start to shut off programs that you're computer is using and you'll see it all happening. That's because Linux is a transparent system. It lets you see everything it's doing. It won't give you a simple message telling you to wait and then another one telling you you can shut it off now. If something is causing a problem, it will tell you about it when it starts up and when it shuts down. That way, if you are having a problem, you may be able to track it down. If you don't know how to solve it, you can tell another person what you saw and he or she may be able to help you.

With the   shutdown -h now   command, you must wait until you see the message:

    System halted

or

    Power down

before you shut off the computer.
Re-booting the computer

The other command that you will probably use is:

      sudo shutdown -r now   

If you have installed a dual-boot system and you want to use the other operating system, (why would you want to do that?) you would use this command. You will get a similar message as with the -h (halt) option that will say something like:

      System going for reboot NOW  

The basic reason behind all of these messages is that Linux was conceived to be a networked operating system. You have people at workstations on the network busily doing their work. The last part of the shutdown command now is fine for a single-user home PC, but on a network system this would be changed to indicate a time. That way people would have a chance to finish what they were doing before the system went down for maintenence. Using 'now', in a network, would probably be hazardous to the health of the person who sent that command.

The next time you shutdown your system, you may want to try using some time options instead of just now. For example, you may want to try shutting down the computer at a given time.

    shutdown -h 20:01 

Which will shutdown the computer at 8:01 PM. You could also try:

    shutdown -h +5 

That shuts down the computer in 5 minutes time.

---

