---
title: "[SOLVED] Login issue"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Norm24 on 2008-12-14
I've apparently changed some setting where I am now logging in full screen terminal.Once logged in I'm in full screen terminal and have full use of the terminal,is there some command I can use to get my desktop back?.I would love to have my desktop back!

I'm not sure what I did but I believe it might have been this:

System>Administration>Login Window>Security

I think I changed something under the security tab.The next time I started Ubuntu the above mention issue happened.

Any help would be highly appreciated.I really miss my desktop!!!

---

### Post by taurus on 2008-12-14
What is the error message when you run this command from a prompt?

```
startx
```

---

### Post by Norm24 on 2008-12-14
> **taurus said:**
> What is the error message when you run this command from a prompt?

```
startx
```

```
start: Unknown Job: x
```

---

### Post by cmnorton on 2008-12-14
What does your /etc/inittab look like? You might have dropped down to an X-term if the run level had been lowered to 3.

---

### Post by taurus on 2008-12-14
> **Norm24 said:**
> ```
start: Unknown Job: x
```

Did you put a space between start and x?  There shouldn't be a space; it's one word--startx.

---

### Post by Norm24 on 2008-12-14
> **cmnorton said:**
> What does your /etc/inittab look like? You might have dropped down to an X-term if the run level had been lowered to 3.

That's beyond my comprehension,but I do recall something when I was "playing"around that involved the word X-term.

What is /etc/inittab?I've noticed there is a bunch of stuff like that when I first load up Ubuntu before the Login lines show up.

---

### Post by Norm24 on 2008-12-14
> **taurus said:**
> Did you put a space between start and x?  There shouldn't be a space; it's one word--startx.


Start: Unknown Job: x was the response to startx.

---

### Post by Norm24 on 2008-12-14
I tried startx again was able regain my desktop.I was then given the messsage that the "user switcher" failed to load.I was given the option to either reload it or quit.I tried several times to do so and it didn't work.

Now I clicked on System>Administration>Login Window and this what I got:

---

### Post by Norm24 on 2008-12-14
I also have lost the ability to shutdown.Have to push the power button.

---

### Post by taurus on 2008-12-14
Try starting the gdm GUI then.

```
sudo /etc/init.d/gdm start
```

---

### Post by Norm24 on 2008-12-14
> **taurus said:**
> Try starting the gdm GUI then.

```
sudo /etc/init.d/gdm start
```

After the unusual text style login that brings me into full screen terminal,I used that code and it worked.But in order start ubuntu in gdm each time I have to type this code in everytime at login.

Now that I have full access again what can I do to make Ubuntu start normally once again?

---

### Post by Norm24 on 2008-12-14
It occurred to me that if I were to restore all the default settings that I should be back to where I was before.

Can't find a way to restore default settings.

---

### Post by cmnorton on 2008-12-15
If you can get GDM running, could you go back to the setting in Administration and try to reconstruct what you changed?

---

### Post by philinux on 2008-12-15
> **Norm24 said:**
> It occurred to me that if I were to restore all the default settings that I should be back to where I was before.

Can't find a way to restore default settings.

If you navigate to youe home folder ctrl h to show hidden files, then delete .gnome and .gnome2 then logout and login You'll get the default desktop. you'll have to re-apply any customisations you might have made.

---

