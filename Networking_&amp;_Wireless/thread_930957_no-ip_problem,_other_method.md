---
title: "no-ip problem, other method"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by Pyro.699 on 2008-09-26
Hello,

Ive ran into a very.... difficult problem to overcome...

I'm developing a web page, that the only user will be me, and maybe a few friends. Ive been given permission by my university to leave my laptop at the school and download all i want but i have to manage it myself. The reason for this is because im on dial-up at home and have absolutly no way of getting it. Im in the 10% of canada that cannot recive highspeed.

Ths problem ive encountered is that i cannot get my webpage to be avaliable to the "public". I dont have access to the router so i cannot configure it. The site is made with a combination of Java (using ROBOT methods), javascript, PHP, MySQL and of course html. The Java portion of the webpage is what controlls the computer without a user being there. It runs applications, simulates a keyboard, simulates the mouse and other input devices. To top it off, theres a method to create a screenshot of the screen and display it. What i need to do is find a way to communicate between the host and the user that allows me to work from my desktop.

I had the idea of connecting to MSN and having the server send messages to my laptop and doing something like that... just an idea

Thankyou very much for your help
~Cody Woolaver

---

### Post by doug-M on 2008-09-27
You could have the laptop retrieve a plain text file from a webserver using wget. The file could contain a list of URLs that the laptop should request using wget. 

If you want interactive control I think you will pretty much have to have the laptop make a connection to somewhere and you make a connection to the same server. Similar to what you are really doing with MSN IM/chat.

Another option would be to have the laptop periodically attempt to initiate a VPN connection to you at home, or to a dynamic DNS entry that you control (such as dyndns.org). Then you let it set up the VPN tunnel for you over your dial up connection and you now have control of the machine.

Take a look at OpenVPN for one way to set up the VPN. 

Not sure if it would definitely work but probably worth a shot.

---

### Post by Pyro.699 on 2008-09-27
Thanks for the idea. Would you, or anyone else know how i could initiate a MSN conversation using java, perl, or even php. Id need 2 accounts, **laptop@domain.com** and **guest@domain.com**, the laptop one could be the receiver of the messages coming from the guest account. The messages could be like: Keyboard:Send:this, and the script could read that as sending **this** to the keyboard method. Remember that this has to be the fastest method posible because dial-up is a pain and i can only connect at 28.8kb/s MAX. Which isnt really fun. Ive looked at documentations online but i think i need someone to explain it to me in a much more elaborated way.

Also, im still open to new ideas if someone wanted to sugguest it.

Thanks
~Cody Woolaver

---

### Post by doug-M on 2008-09-28
The VPN connection might be a better solution, once the VPN is set up you can do do an ssh connection and get a shell to do anything you want. All that would work quite nicely over a modem.

For that matter you could attach a modem to the laptop and dial into it.

---

### Post by Pyro.699 on 2008-09-28
How exactly would that work? because that would require me to plug into the schools phone line correct?

---

### Post by doug-M on 2008-09-28
Yes you would need a phone line that the modem could answer or that it could dial out on (and dial you).

---

### Post by doug-M on 2008-09-28
Another option would be to email information for it.
Have an email account that it can read and parse the commands out of.

You might consider doing something like digitally signing the commands or the email to make sure nobody else makes it do stuff since effectively what you are doing is making a botnet zombie.

---

### Post by Pyro.699 on 2008-09-28
> **doug-M said:**
> Another option would be to email information for it.
Have an email account that it can read and parse the commands out of.

You might consider doing something like digitally signing the commands or the email to make sure nobody else makes it do stuff since effectively what you are doing is making a botnet zombie.
that would be a neat idea except for the fact that the server would have to constantly check for new emails and im trying to make the transsision between server as quick as possible

---

### Post by doug-M on 2008-09-28
Well you implied earlier that the machine was there to download stuff. If that isn't the case what do you want to do with it that requires almost interactive access?

---

### Post by Pyro.699 on 2008-09-28
Yes, i already have all the java modules constructed to allow access to any part  of the system. I need to find the most productive way to connect my computer to a guest one. Ive learned that alot of port are closed, but i can still torrent and msn so there are some open. I have a feeling the university wouldnt allow me to plug into a phone line though

---

