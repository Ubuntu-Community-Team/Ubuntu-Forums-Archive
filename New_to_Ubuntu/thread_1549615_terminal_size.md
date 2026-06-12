---
title: "terminal size"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by 007casper on 2010-08-10
when I use the terminal, if the path of the file is long, the terminal starts to write the text on top of each other without making any break/carriage.  

How can I change the terminal size?  I went full screen it didnt help at all.  Is there direct correlation with the server monitor size set up and the terminal size?

thank you

---

### Post by Clever_Username on 2010-08-10
Click on "terminal" at the top and you should be able to change the settings from there. If the menu bar isn't there, right click in an open area of the terminal, and you'll see a setting for "show menu bar".
Hope this helps

---

### Post by 007casper on 2010-08-10
thanks.  I am actually over at putty.

I went to Putty configuration and click on window.  I have set columns 150 rows 40... it still has the same issue.  I have putty release .60

if I can get rid of this issue, it will be so awesome, so I can see what I am typing.

---

### Post by pzico on 2010-08-10
Could you try:
export PS1="\n\[\e[0;36m\]$ \W> \[\e[m\]"

On bash the readline can easily lose track of the column position. I don't recommend that as default prompt, but it might solve your problems.

---

### Post by 007casper on 2010-08-11
thank you... thank you ~ 
I just tried that on a different server.  I think it might work...  I am definitely going to try this when the text goes up on each other again.

why wouldnt you try it as default?

---

### Post by sandyd on 2010-08-11
> **007casper said:**
> thank you... thank you ~ 
I just tried that on a different server.  I think it might work...  I am definitely going to try this when the text goes up on each other again.

why wouldnt you try it as default?
If you want to try it as default, stick it into ~/.bashrc

---

### Post by pzico on 2010-08-12
> **007casper said:**
> thank you... thank you ~ 
I just tried that on a different server.  I think it might work...  I am definitely going to try this when the text goes up on each other again.

why wouldnt you try it as default?

Because some purist will come and kill me for using Windows/DOS style ">" as the last character in prompt instead of "$". :-$

However, I believe the issue you have is more about control characters, please modify given PS for your taste :popcorn:

---

### Post by 007casper on 2010-08-14
Thats funny.  

It works like a charm.  

Thank you so much. ~:)

---

