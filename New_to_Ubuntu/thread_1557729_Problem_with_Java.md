---
title: "Problem with Java"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by hamstermoon on 2010-08-21
It's this daft Chinese Dictionary again ...

[http://www.yellowbridge.com/chinese/chinese-dictionary.php](http://www.yellowbridge.com/chinese/chinese-dictionary.php)

When I put a word in the English to Chinese box (say "thousand") when I get to click on the stroke order I can't see the amimation.

I am getting this message both on Firefox and on Chromium and am not sure what to do about it:

"Got  a Java security warning, asking you whether to "Block    potentially
unsafe components from being run?" Click on No to proceed.
If animation does not start after 2 sec, click on **Animate**.
*Animation window not drawn altogether?* Try updating    your Java."

Java is not giving me any options to do anything (no windows or boxes come up) so I can't fix it.nThe animation is definitely not playing which is a bit of a pain. Anyone got any suggestions? How DO I update Java anyway??

---

### Post by jonnywombat on 2010-08-21
I followed your instruction and reproduced your problem.

Which version of java do you use?

easy way to tell is to fire up the software centre and search for java... I have the openJDK installed atm, and i guess you will too.

It would probably be beneficial to uninstal openJDK java, and replace it with Sun Java. This can all be done within the software centre.

hth

---

### Post by jonnywombat on 2010-08-21
I have made the changes I described in previous post and can confirm it fixes your problem.

Once you have checked it works for you too please mark thread as solved, using the thread tools.

---

### Post by hamstermoon on 2010-08-21
I will have to get help from my friend who knows how to do that as I Googled how to do it and but I can't seem to get my computer to do what it says. Many thanks for the help and I will change this to 'solved' once I know its working.

---

### Post by jonnywombat on 2010-08-21
On your main menu select ubuntu software centre.

Once it loads in the top right corner there is a search box. In it type java.

At the top of the list that appears you will see the java you have installed, this is shown by a tick in a green circle

It should say openJDK java. If so click on the remove. A box will pop up saying you must remove a load of other packages, click ok and let it do it's stuff.

Once finished click on the edit tab of the software centre, and select software sources from the bottom of the list that opens. You will be prompted for your password.

On the new window that opens click on the tab marked other software, and make sure that the top entry which reads "http://archive.canonical.com/lucid partner" is selected. If it is not then check the box next to it to enable it.

Click close. If you have had to add the partner source then an update of your sources will take place, just let it run, you may be prompted for your password again.

Ok now your on the home stretch...

Back to the search box in the top right corner of the software centre.. type in sun java. look for an entry called sun java runtime environment and select it and click install. Once that has run, make sure all internet browsers are closed. Then click on Sun java 6 plugin and install that too.

Now you should be good to go.

HTH

---

### Post by philinux on 2010-08-21
Works ok here with sun java. Version 6 Update 21

---

### Post by hamstermoon on 2010-08-22
My friend Kevin very kindly talked me through it over the phone and we did exactly what Jonnywombat suggested. Thank you = it works now.  :KS:KS:KS

---

