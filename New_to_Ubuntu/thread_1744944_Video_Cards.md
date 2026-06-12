---
title: "Video Cards"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by daniell59 on 2011-04-30
Please forgive me if this is an inane question.
What is the significance of the different video cards.
I know that my system functions best with none selected in Visual Effects.
This is my Video Card. Asus EAH3450

Thanks

---

### Post by K_45 on 2011-04-30
That card with fglrx driver should work with desktop effects. There are a number of differences in GPU's, such as ROP's, texture units, clock speed, API support, but this shouldn't effect desktop effects. Ubuntu is not Windows in terms of resources (yet).

---

### Post by daniell59 on 2011-04-30
> **K_45 said:**
> That card with fglrx driver should work with desktop effects. There are a number of differences in GPU's, such as ROP's, texture units, clock speed, API support, but this shouldn't effect desktop effects. Ubuntu is not Windows in terms of resources (yet).

Whenever I would choose anything except none, I would have a problem going from one window to another one. Why, I don't know.

---

### Post by K_45 on 2011-04-30
Have you tried the proprietary driver?

---

### Post by daniell59 on 2011-04-30
> **K_45 said:**
> Have you tried the proprietary driver?

I think that I did.

---

### Post by K_45 on 2011-04-30
Enter   

```
fglrxinfo
```

in a terminal, what is the output?

---

### Post by daniell59 on 2011-04-30
> **K_45 said:**
> Enter   

```
fglrxinfo
```

in a terminal, what is the output?

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3400 Series
OpenGL version string: 3.2.9756 Compatibility Profile Context

---

### Post by K_45 on 2011-04-30
You are using the driver, but effects can't be enabled? What is the exact problem?

---

### Post by daniell59 on 2011-04-30
> **K_45 said:**
> You are using the driver, but effects can't be enabled? What is the exact problem?

When I have more than one window open, and I want to go to another one, the response is very sluggish. It may take several seconds to respond.
When none is selected, I have no problme.

---

### Post by the-penguin on 2011-04-30
It sounds like this could be the RAM, since the video card is supported and quite powerful.
How much RAM does your computer have?
If you don't know you can find it in the System Monitor, it's usually just listen as Memory.

regards,
Jason

---

### Post by daniell59 on 2011-04-30
> **the-penguin said:**
> it sounds like this could be the ram, since the video card is supported and quite powerful.
How much ram does your computer have?
If you don't know you can find it in the system monitor, it's usually just listen as memory.

Regards,
jason

4gig

---

### Post by K_45 on 2011-04-30
What are your system specs? PC/laptop?

Run ```
sudo lshw -html > results.html
```

Open the html file and note down the specs.

---

### Post by daniell59 on 2011-04-30
> **K_45 said:**
> What are your system specs? PC/laptop?

Run ```
sudo lshw -html > results.html
```

Open the html file and note down the specs.

How do I open the HTML file?

---

### Post by K_45 on 2011-04-30
Firefox or Chromium. Double click on it.

---

### Post by daniell59 on 2011-04-30
> **K_45 said:**
> Firefox or Chromium. Double click on it.

I am sorry but I am not following you. Do I double click in the terminal?

---

### Post by K_45 on 2011-04-30
Run

```
firefox results.html &
```

---

### Post by daniell59 on 2011-04-30
> **K_45 said:**
> Run

```
firefox results.html &
```

Thanks for your input, I will read what you have suggested.

---

