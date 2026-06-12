---
title: "Amarok"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-06
I've just recently installed Amarok 2.0 Beta 2, and I'm kind of confused about a couple of things.

- Can I transfer music from my iPod (from amarok) to my desktop? I thought this was possible by just dragging and dropping from amarok to the desktop, but this does not seem to be the case.

- Is there a way I can save changes I made to my iPod on Amarok? 
For example, I changed the various cases 'Immortal Technique' was spelled in so it doesn't show as different artists, but when I unplugged my ipod and plugged it back in, it was back to how it was previously.

---

### Post by bhadotia on 2008-12-06
> **adobrakic said:**
> I've just recently installed Amarok 2.0 Beta 2, and I'm kind of confused about a couple of things.

- Can I transfer music from my iPod (from amarok) to my desktop? I thought this was possible by just dragging and dropping from amarok to the desktop, but this does not seem to be the case.

- Is there a way I can save changes I made to my iPod on Amarok? 
For example, I changed the various cases 'Immortal Technique' was spelled in so it doesn't show as different artists, but when I unplugged my ipod and plugged it back in, it was back to how it was previously.

Open your ipod in your file browser and then you can transfer/alter files in the same way you copy, rename and move files between different folders.

---

### Post by adobrakic on 2008-12-06
I think I found the songs, but they're titled 'gtkpod######.mp3'

---

### Post by bhadotia on 2008-12-07
> **adobrakic said:**
> I think I found the songs, but they're titled 'gtkpod######.mp3'

Actually I've never had a an ipod, so I can't help you further. Whenever I trnsfer music to my cellphone I use this method, and this works fine for me.

---

### Post by steveprevoni on 2008-12-07
Use the program GTKPod it loads your ipod automatic and you can simply click and drag onto and off your ipod

---

### Post by adobrakic on 2008-12-07
something tells me you didn't read the posts

---

### Post by bhadotia on 2008-12-07
> **adobrakic said:**
> something tells me you didn't read the posts

Ya! try gtkpod. I think that is the reason for the songs being named gtkpod*** etc.
Type this in the terminal (Applications>Accessories>Terminal):
```
sudo apt-get install gtkpod gtkpod-aac
```

---

### Post by Paqman on 2008-12-07
> **adobrakic said:**
> 
For example, I changed the various cases 'Immortal Technique' was spelled in so it doesn't show as different artists, but when I unplugged my ipod and plugged it back in, it was back to how it was previously.

What did you change? The file names, the ID3 tags, or both?

---

### Post by adobrakic on 2008-12-07
> **bhadotia said:**
> Ya! try gtkpod. I think that is the reason for the songs being named gtkpod*** etc.
Type this in the terminal (Applications>Accessories>Terminal):
```
sudo apt-get install gtkpod gtkpod-aac
```

```

ado@ado-desktop ~ $ sudo apt-get install gtkpod gtkpod-aac
[sudo] password for ado: 
Sorry, try again.
[sudo] password for ado: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtkpod is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtkpod-aac: Conflicts: gtkpod
E: Broken packages
ado@ado-desktop ~ $ 

```

> 
What did you change? The file names, the ID3 tags, or both? 


Just the ID3 tags, im pretty sure.
idk what amarok edits by default, but i think its the id3 tag

---

### Post by bhadotia on 2008-12-07
> **adobrakic said:**
> ```

ado@ado-desktop ~ $ sudo apt-get install gtkpod 
[sudo] password for ado: 
Sorry, try again.
[sudo] password for ado: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtkpod is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtkpod-aac: Conflicts: gtkpod
E: Broken packages
ado@ado-desktop ~ $ 

```



Just the ID3 tags, im pretty sure.
idk what amarok edits by default, but i think its the id3 tag

```
sudo apt-get install gtkpod
```
Try this.

---

### Post by adobrakic on 2008-12-07
Yeah, I already have gtkpod. It works fine with detecting my songs on the iPod and stuff, and it even displays the correct names of the songs and everything.
Just that when i transfer it from gtkpod to my desktop, the songs change to 'gtkpod321312.mp3'

---

### Post by bhadotia on 2008-12-07
> **adobrakic said:**
> Yeah, I already have gtkpod. It works fine with detecting my songs on the iPod and stuff, and it even displays the correct names of the songs and everything.
Just that when i transfer it from gtkpod to my desktop, the songs change to 'gtkpod321312.mp3'

Thats because you are using gtkpod to transfer the songs. If you use the file browser, I think, that they will show correct names.

---

### Post by stokedfish on 2008-12-10
2.0 has landed...

[http://amarok.kde.org/en/releases/2.0](http://amarok.kde.org/en/releases/2.0)

---

### Post by adobrakic on 2008-12-10
ballin!

---

