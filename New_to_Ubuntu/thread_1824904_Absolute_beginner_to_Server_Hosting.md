---
title: "Absolute beginner to Server Hosting"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Jakemurray on 2011-08-14
Hi, i have been interested in starting up a website of my own, but i want to host it on my own personal server.
unfortunately i have absolutely no experience with servers, and i dont even know where to begin.
i have done some reading up and i think my choice will be a LAMP server.
now to the question, lets assume that i know nothing but html, css, JS, etc. where would be the best place to start learning about servers, how to operate within a server, and the such? and which ubuntu server OS would be the best choice?
any help would be very much appreciated, i will also post my email address for an alternate method of communication. thank you so much.

[EMAIL="jake.murray81@hotmail.com"]jake.murray81@hotmail.com[/EMAIL]

---

### Post by spiky001 on 2011-08-14
Dont know your experiance on linux but SECURITY would be good to learn especuraly as your hosting

---

### Post by HermanAB on 2011-08-14
Howdy,

If you still have no clue what you are doing, just use ordinary desktop Ubuntu.

---

### Post by Insomnia64 on 2011-08-14
In my experience at least a server running ubuntu is no different from my desktop ubuntu when i'm in a terminal (more or less), so i'm not sure what you mean in regards to "learning about servers". If you mean the server processes of HTTP responses and such then wikipedia would be a good place to start. Otherwise i'd advise just setting up a LAMP server on your desktop and trying it.

For a guide on LAMP setup I found [this]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") guide very good. Just be aware that the mysql installation is a bit different now and it does all the password settings during the install for you, so skip step 3.

After that [w3schools]("http://www.w3schools.com/") do good tutorials to get you started on HTML and CSS, it all goes in /var/www and you should then be able to access it by going to localhost in your browser of choice.

---

### Post by Jakemurray on 2011-08-14
> **Insomnia64 said:**
> In my experience at least a server running ubuntu is no different from my desktop ubuntu when i'm in a terminal (more or less), so i'm not sure what you mean in regards to "learning about servers". If you mean the server processes of HTTP responses and such then wikipedia would be a good place to start. Otherwise i'd advise just setting up a LAMP server on your desktop and trying it.

For a guide on LAMP setup I found [this]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") guide very good. Just be aware that the mysql installation is a bit different now and it does all the password settings during the install for you, so skip step 3.

After that [w3schools]("http://www.w3schools.com/") do good tutorials to get you started on HTML and CSS, it all goes in /var/www and you should then be able to access it by going to localhost in your browser of choice.
what i mean by learning about servers is im trying to know how to operate a server, i dont know how to with the terminal either, im a total newbie to hosting a site =/ its quite discouraging really lol but thanks for the links ill definitely check them out

---

### Post by Jakemurray on 2011-08-14
i also just installed apache2 and i tested it and got the "it works" page, which is good, but where do i put all of my source for the actual website?

---

### Post by Insomnia64 on 2011-08-14
Well on my server i've got ubuntu server installed, which works just like ubuntu desktop except comes with different packages installed by default (no GUI etc.)

In which case all you'd need to do is learn how to work with the terminal, which just takes a bit of practice. Not sure of any web links for that off the top of my head though typing ```
man <operation you'd like ot know more about>
``` will bring up it's manual and you can learn from there.

Or if you'd prefer a guide i purchased a book "Linux phrasebook" which taught me a lot even though i'd have said i was reasonably proficient!

Edit: your source goes in /var/www, if you look in there you'll see a page called index.html and that is the "It works!" page.

---

### Post by Jakemurray on 2011-08-14
i know this is probably the biggest newbie question youll ever hear but how do i find /var/www. im guessing its a folder?
im still getting used to navigating and finding things in ubuntu.

---

### Post by Insomnia64 on 2011-08-14
From the UI: Click on 'Places' on the menu bar (if you're on 11.04 i've no idea, never used unity before sorry!) go to 'Computer'.
Click on 'File system' and that will bring you to the highest level of your file system, which is /

In here you will see a folder called 'var'.

If you want to get to it from the terminal type:```
cd /var/www
```

---

### Post by Jakemurray on 2011-08-14
Great!! i found it, im using 11.04 but i went back to the gnome interface 
Thank you so much for your help i really really appreciate it!
if its not too much of a hassle could i friend you in case i have any other trouble?

---

### Post by Insomnia64 on 2011-08-14
Sure, no problem :)

---

### Post by Elfy on 2011-08-14
Thread closed. Please do not post duplicates, it dilutes community effort.

---

