---
title: "fairly simple question (HTML)"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by gfunkera on 2009-05-12
i wrote a page that has a few buttons that the user can click on to access different pages... each button is treated as an individual form that posts to a particular, corresponding page.
 
when i view the page on my ubuntu machine in firefox, the buttons are all side by side with no page breaks between them. as they should be.
 
when i view the page from my vista (IE explorer) machine at work or at a friends computer, the buttons are stacked on top of eachother..
 
how can i avoid this?

---

### Post by lykwydchykyn on 2009-05-12
Can you give an idea of how the code looks?  Are you using style sheets, or just html?

With CSS, you can just specify "display:inline" and it should have them all next to each other.  Where you put that depends on how you are handling styles.

For example, you can put something like this in the head portion of your HTML:
```

<style>
BUTTON { display: inline; }
</style>

```

Or you can do your button tags like this:
```

<button style="display:inline;">

```


Of course, you can always be retro about it and put them in a table. ;-)

---

### Post by gfunkera on 2009-05-12
thanks for yourhelp! im using CSS...
 
i am kinda of an old school dude and i think ill go the retro route adding a table.. how do i remove borders on the table completely, please?

---

