---
title: "Default permissions for 'media' folder"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by avnd on 2011-07-13
Hello!

I was trying to change the permissions for a folder I had mounted to the 'media' folder in the Ubuntu filesystem. I was following a guide and the command I had to enter was the following

"sudo chmod 777 /media/GRUBpartition/boot/grub/menu.lst"

Unfortunately, I accidentally pressed 'Enter' when I got to,
"sudo chmod 777 /media/"

Can anyone tell me what would've happened and tell me what I can do to restore them to the default state?

Thanks!
Cheers!

---

### Post by MG&amp;TL on 2011-07-13
I don't suppose you remember what the terminal said after you entered the command? If you're lucky, there'll be a reason why it couldn't do anything and nothing will have happened. :) In theory, anyway. People better qualified than me can answer this in one go, I'm just 'getting my eye in' with these forums...:)

---

### Post by coffeecat on 2011-07-13
> **avnd said:**
> Unfortunately, I accidentally pressed 'Enter' when I got to,
"sudo chmod 777 /media/"

Can anyone tell me what would've happened and tell me what I can do to restore them to the default state?


You would have assigned 777 permissions to /media! No - let me rephrase that. You **have** assigned 777 permissions to /media/. You get no feedback - the bash terminal will have done the deed and silently returned the prompt. And this all means that the world and their auntie can now write to /media. 

But fear not! :wink: To get the /media folder back to its default state, simply:

```
sudo chmod 755 /media
```

If you want to see what the permissions are now, and also after you run the chmod 755 command, run:

```
ls -l /
```

... and look for the /media line.

---

### Post by avnd on 2011-07-13
> **coffeecat said:**
> You would have assigned 777 permissions to /media! No - let me rephrase that. You **have** assigned 777 permissions to /media/. You get no feedback - the bash terminal will have done the deed and silently returned the prompt. And this all means that the world and their auntie can now write to /media. 

But fear not! :wink: To get the /media folder back to its default state, simply:

```
sudo chmod 755 /media
```If you want to see what the permissions are now, and also after you run the chmod 755 command, run:

```
ls -l /
```... and look for the /media line.

Thanks for your replies, MG&TL and Coffeecat.  I kinda knew the permissions had changed to the media folder. But I didn't know what the default permissions were so that I could restore them to how they were.  Thanks again, fellas!

---

### Post by MG&amp;TL on 2011-07-13
No problem, agvn. Coffecat is awesome, he/she (no offence intended cc, it's just that your avatar and writing style aren't particularly enlightening) has helped me numerous times. :D

It's good practice to mark 'dead' threads as [SOLVED] (hint, hint) :)

---

