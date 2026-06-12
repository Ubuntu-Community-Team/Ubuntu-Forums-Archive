---
title: "UBUNTU firewall does not has Application control"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Adi100 on 2009-11-28
Hi to every one.

the Firestarter in UBUNTU does has provision for opening or closing the ports for inbound and outbound connections.

However it lacks features such as Application control which are found in windows firewall and third party firewall for windows.

-when such feature will be available in UBUNTU firewall, As we can see more people( mainly Home user not the corporate desktop deployment) will move to UBUNTU in near future.

Regards

Adi

---

### Post by pbrane on 2009-11-28
I don't use FireStarter, I found it not as good as **ufw**.

I'm not exactly sure what you mean by application control, but **ufw** does have application integration. I use **ufw** to allow specific applications access to my network. 

There is more than one firewall available to GNU/Linux systems.

---

### Post by mkvnmtr on 2009-11-28
I found that I was much happier the day I uninstalled FireStarter. The default works fine and the more you mess with it the less secure you will probably be.

---

### Post by 3rdalbum on 2009-11-28
> **Adi100 said:**
> Hi to every one.

the Firestarter in UBUNTU does has provision for opening or closing the ports for inbound and outbound connections.

However it lacks features such as Application control which are found in windows firewall and third party firewall for windows.

-when such feature will be available in UBUNTU firewall, As we can see more people( mainly Home user not the corporate desktop deployment) will move to UBUNTU in near future.

Regards

Adi

1. You don't actually need a personal firewall on Ubuntu. It doesn't have any open ports by default. There are a small number of use cases for a personal firewall, but this always involves you running server services (we're talking about home users, remember) and NOT being behind a broadband router. Who do you know who runs server software on mobile broadband and dialup?

Windows requires a firewall because it listens to incoming connections in the default install. This is insecure and unsafe, not to mention just completely stark raving bonkers.

2. Ordinary home users don't want to be bothered with prompts all the time whenever a program tries to connect to the Internet. People often ask me how to disable that part of their Internet Security suite. Ordinary home users also don't want to, nor have the knowledge to, set up application rules.

3. Ubuntu has extra security in place to prevent internet-facing services from being able to access your user data anyway, which means if a program was compromised and "phoned home", it wouldn't be able to provide the attacker with any useful information. This protection happens silently.

4. Windows' lack of security (need for a firewall out-of-the-box, plus anti-virus etc) is partly what drives people to Linux.

---

