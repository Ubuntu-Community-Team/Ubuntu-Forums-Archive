---
title: "CSS not rendering properly in firefox on ubuntu"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by jarongg on 2009-02-24
any ideas how i can fix this?

---

### Post by kellemes on 2009-02-24
> **jarongg said:**
> any ideas how i can fix this?

You're not really giving info for us to work with..
What's not going right?
Any screenshots?
Any links to sites where rendering goes wrong?

---

### Post by jarongg on 2009-02-24
yea, sorry. here is how it looks:

[http://img.photobucket.com/albums/v497/jarong/Screenshot-1.png](http://img.photobucket.com/albums/v497/jarong/Screenshot-1.png)

[http://img.photobucket.com/albums/v497/jarong/Screenshot-1-1.png](http://img.photobucket.com/albums/v497/jarong/Screenshot-1-1.png)




and here is how it should look:

[http://img.photobucket.com/albums/v497/jarong/Screenshot-2.png](http://img.photobucket.com/albums/v497/jarong/Screenshot-2.png)

---

### Post by crjackson on 2009-02-24
What browser are you using in the properly formatted screenshot?

---

### Post by jarongg on 2009-02-24
epiphany.

---

### Post by crjackson on 2009-02-24
> **jarongg said:**
> epiphany.

I don't have an answer to your question but I have had some pages like that too.

I'm going to have a look at it myself when I get home from work and it looks like I too may need to install epiphany.

---

### Post by amauk on 2009-02-24
[http://validator.w3.org/check?uri=http%3A%2F%2Fboard.vivalavinyl.org%2F&charset=(detect+automatically)&doctype=Inline&group=0&accept=text%2Fhtml%2Capplication%2Fxhtml%2Bxml%2Capplication%2Fxml%3Bq%3D0.9%2C*%2F*%3Bq%3D0.8&accept-language=en-gb%2Cen%3Bq%3D0.5&accept-charset=ISO-8859-1%2Cutf-8%3Bq%3D0.7%2C*%3Bq%3D0.7&user-agent=W3C_Validator%2F1.606](http://validator.w3.org/check?uri=http%3A%2F%2Fboard.vivalavinyl.org%2F&charset=(detect+automatically)&doctype=Inline&group=0&accept=text%2Fhtml%2Capplication%2Fxhtml%2Bxml%2Capplication%2Fxml%3Bq%3D0.9%2C*%2F*%3Bq%3D0.8&accept-language=en-gb%2Cen%3Bq%3D0.5&accept-charset=ISO-8859-1%2Cutf-8%3Bq%3D0.7%2C*%3Bq%3D0.7&user-agent=W3C_Validator%2F1.606)

[http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fboard.vivalavinyl.org%2F&profile=css21&usermedium=all&warning=1&lang=en](http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fboard.vivalavinyl.org%2F&profile=css21&usermedium=all&warning=1&lang=en)

---

### Post by jarongg on 2009-02-24
> **amauk said:**
> [http://validator.w3.org/check?uri=http%3A%2F%2Fboard.vivalavinyl.org%2F&charset=(detect+automatically)&doctype=Inline&group=0&accept=text%2Fhtml%2Capplication%2Fxhtml%2Bxml%2Capplication%2Fxml%3Bq%3D0.9%2C*%2F*%3Bq%3D0.8&accept-language=en-gb%2Cen%3Bq%3D0.5&accept-charset=ISO-8859-1%2Cutf-8%3Bq%3D0.7%2C*%3Bq%3D0.7&user-agent=W3C_Validator%2F1.606](http://validator.w3.org/check?uri=http%3A%2F%2Fboard.vivalavinyl.org%2F&charset=(detect+automatically)&doctype=Inline&group=0&accept=text%2Fhtml%2Capplication%2Fxhtml%2Bxml%2Capplication%2Fxml%3Bq%3D0.9%2C*%2F*%3Bq%3D0.8&accept-language=en-gb%2Cen%3Bq%3D0.5&accept-charset=ISO-8859-1%2Cutf-8%3Bq%3D0.7%2C*%3Bq%3D0.7&user-agent=W3C_Validator%2F1.606)

[http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fboard.vivalavinyl.org%2F&profile=css21&usermedium=all&warning=1&lang=en](http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fboard.vivalavinyl.org%2F&profile=css21&usermedium=all&warning=1&lang=en)

so you're telling me the problem lies within how they wrote it, and not my browser?

---

### Post by simeon87 on 2009-02-24
> **jarongg said:**
> so you're telling me the problem lies within how they wrote it, and not my browser?

Yes, there are 426 errors and 420 warnings for the XHTML and 14 errors and 144 warnings for the CSS... nothing can save you from that ;)

---

### Post by amauk on 2009-02-24
I think so
(I say "think", as the actual page looked nothing like your screenshot - is it different for logged in users?)

I think the issue is differing browser behaviour when presented with invalid markup

the CSS validator certainly threw up some errors for positioning properties

---

### Post by jarongg on 2009-02-24
> **amauk said:**
> I think so
(I say "think", as the actual page looked nothing like your screenshot - is it different for logged in users?)


yea, all the screenshots are from when i am logged in. if you were to visit the page yourself, it would look differently to you.

i have tried a few browsers since i made this thread, and it is funny how almost all of them work, except for firefox. i am going to try firefox 2 in a second, and see if that is any better.

---

### Post by jarongg on 2009-02-24
firefox 2 works as well.

---

### Post by crjackson on 2009-02-24
> **jarongg said:**
> firefox 2 works as well.

I've had problem with banking sites on FF3. Perhaps the fix IS FF2.

I don't understand why it's the websites fault if most browsers DON'T have a problem.

---

