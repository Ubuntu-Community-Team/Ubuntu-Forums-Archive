---
title: "help wih .sh"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by lakofrune on 2010-03-09
the file extension is .sh    how do i install it or "execute" it? or what is it.

---

### Post by wojox on 2010-03-09
It's a shell script that needs it's permissions set before you run. Before we get into that what is it you downloaded?

---

### Post by lakofrune on 2010-03-09
to be specific its a runescape bot, supposedly compatible with linux. i had it on windows before i made the switch. i trust it.

---

### Post by wojox on 2010-03-09
Try:

```
sudo chmod +x filename.sh
```

Then:

```
./filename.sh
```

Remember you need to be in the directory the script is in or else set it's path accordingly.

---

### Post by Dayofswords on 2010-03-09
i want to throw in this

runescape bots are against the rules of the game(i play it)

[http://www.runescape.com/rules/rule_third_party_software.ws](http://www.runescape.com/rules/rule_third_party_software.ws)


with a quick 2 posts, i have an instant dislike of you...
your what ruins the game for some...

---

### Post by lakofrune on 2010-03-09
sweet thanks!

---

### Post by mkvnmtr on 2010-03-09
On my system I can right click on a .sh file and it gives me the option to run it. if I do a little terminal opens and it runs. 
I have no idea if this is because of something I have installed or is default .

---

