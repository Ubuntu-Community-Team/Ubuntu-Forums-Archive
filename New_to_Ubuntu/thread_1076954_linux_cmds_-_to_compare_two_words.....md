---
title: "linux cmds - to compare two words...."
date: 2009-02-21
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-02-21
i bought a linux commmands book to learn./

and now , i need to know how to compare two given words/.

like
> 
$word1=kimi
$word2=krishna

now how to compare word1 and word2 , 
and show the result as "both are same" or "both are different"

---

### Post by Old *ix Geek on 2009-02-21
Just test the two values:

```
word1=kimi
word2=krishna
if [ "$word1" = "$word2" ]
then echo "They're the same"
else echo "They're different"
fi

```

---

### Post by kimikrishna on 2009-02-21
> if [ "$word1" = "$word2" ]


after  i enter this,
each line comes with > ,
>
>
>
and i dont know what to do more

---

### Post by kimikrishna on 2009-02-21
oh ! i understood.
i have to enter if , else commands there.....
> 
But even i enter two words are same....

it says "different" 

---

### Post by Old *ix Geek on 2009-02-21
That's just a secondary prompt; type each line and hit [Enter].  After the line containing 'fi' you'll go back to your regular prompt.

---

### Post by Old *ix Geek on 2009-02-21
You're probably not typing it exactly as shown!  Are you leaving off the dollar sign, $?

Make sure that you DO NOT use a $ when defining the values for each variable, but DO use a $ when comparing their values.

Just type it exactly as shown and post back!

---

### Post by kimikrishna on 2009-02-21
thanks..

i got it !! 

ubu rocks !

---

### Post by Old *ix Geek on 2009-02-21
You're welcome. :)

---

