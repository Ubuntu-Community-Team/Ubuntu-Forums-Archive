---
title: "Login Screen Question"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by merlin_ie on 2009-09-11
Hey everyone. I'm really hoping someone can help me with this. I'm making custom login screens and I was wonderin if there is a way to change the text that appears on login failure..the "Incorrect username or password. Letters must be typed in the correct case" text that is. I've looked in the coding and it says something about "pam error" (i think, not on ubuntu at moment) I would like it to say "incorrect password, try again" or something so it will fit the layout of my login screen. Thanks for reading :)

---

### Post by nandemonai on 2009-09-12
> **merlin_ie said:**
> Hey everyone. I'm really hoping someone can help me with this. I'm making custom login screens and I was wonderin if there is a way to change the text that appears on login failure..the "Incorrect username or password. Letters must be typed in the correct case" text that is. I've looked in the coding and it says something about "pam error" (i think, not on ubuntu at moment) I would like it to say "incorrect password, try again" or something so it will fit the layout of my login screen. Thanks for reading :)

This should do the trick:

```
<item type="rect" id="pam-error">
    <pos anchor="c" x="50%" y="35%" width="box" height="box"/>
    <box orientation="vertical" min-width="500" xpadding="10" ypadding="5" spacing="0">
      <item type="label" id="pam-error">
        <normal color="#eeeeee" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
        <text>INSERT TEXT HERE</text>
      </item>
    </box>
  </item>
```

I've taken the above from one of the Linux Mint GDM themes. The important bit is the <text></text> line.

---

### Post by merlin_ie on 2009-09-17
cheers for the reply nandemonai. i´ll give it a try when i get home :)

Edit : ok, i tried what you said, and i changed the " INSERT TEXT HERE " part, but all that did was add something else to the login. maybe i didnt explain clearly enough so ill add an image i just found and then hopefully it will explain better

[IMG]http://www.tuxradar.com/files/LXF109.errors.password_03.jpg[/IMG]

It's that part of the text i want to change. the code you gave me, i used that in the xml and when i went to login, it said " INSERT TEXT HERE " and then disappeared as i typed my name. i dont want anything on screen expect "username and password" like normal login. but when mistake is made, i want a custom message to appear. hope this make more sense

---

