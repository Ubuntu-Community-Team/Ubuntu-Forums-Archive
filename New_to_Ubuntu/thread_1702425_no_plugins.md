---
title: "no plugins?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by maryb on 2011-03-07
I just got a dell computer with ubuntu, it will not play mp3's or any other music. I have no idea how to fix this, help please?

---

### Post by andymorton on 2011-03-07
> **maryb said:**
> I just got a dell computer with ubuntu, it will not play mp3's or any other music. I have no idea how to fix this, help please?

Install the Ubuntu Restricted Extras package from the software centre. It includes MP3 support

andy

---

### Post by marl30 on 2011-03-07
Due to copyright restriction, Ubuntu is unable to ship with all the codecs out the box. Just do what the user above suggest and you'll be able to player all your media files.

---

### Post by maryb on 2011-03-07
wow! ive been searching for days and thats all its going to take?! haha. but my software center wont open now..

---

### Post by marl30 on 2011-03-07
> **maryb said:**
> wow! ive been searching for days and thats all its going to take?! haha. but my software center wont open now..

You can also install it from Synaptic Package manager. Afterwards, try restarting, then check your software center if it's opening ok.

---

### Post by marl30 on 2011-03-07
> **maryb said:**
> wow! ive been searching for days and thats all its going to take?! haha. but my software center wont open now..
Lol :) and that is why using this forum comes in handy. It helps you to know your way around much quicker.

---

### Post by maryb on 2011-03-07
i just restared it, it still doesnt open and when i tried the synaptic package manager, it gave me a error thing say no package was selected or something. I tried to  copy it to here, but it wouldnt work :[

---

### Post by wojox on 2011-03-07
Open your terminal:

```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Sef on 2011-03-07
> Code:
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras

Copy and paste those commands in the terminal, if you do not want to type them out. (Applications > Accessories > Terminal)

If you get any errors, then copy and paste them here.

---

### Post by maryb on 2011-03-07
thank yall so much!!! i have been trying that code for the past two days, and i dont know whats different now but it did more than before! but what do i do once i get to where it has the Package Configuration? i cant get it past there.

---

### Post by marl30 on 2011-03-07
> **maryb said:**
> thank yall so much!!! i have been trying that code for the past two days, and i dont know whats different now but it did more than before! but what do i do once i get to where it has the Package Configuration? i cant get it past there.
Could you explain a bit more so we can know exactly where you're stuck at?

---

### Post by maryb on 2011-03-07
nevermind it works!!!!!!!!! thank u so much!

---

### Post by marl30 on 2011-03-07
If you're talking about the part where it ask you to validate, just click the arrow buttons on your keyboard until it gets to ok then click enter.

---

