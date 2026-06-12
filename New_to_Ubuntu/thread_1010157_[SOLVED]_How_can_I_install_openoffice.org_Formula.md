---
title: "[SOLVED] How can I install openoffice.org Formula?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by crjackson on 2008-12-13
Here's the story. A while back, I added the open-office repos to my Intrepid install so I could upgrade of 3.0.  It worked just fine but apparently there was something wrong with the repo because it was taken down for a bit.

Then the repos was back on line and several updates for OO were available. I couldn't get the updates because it told me I had to do a partial upgrade. If I selected that, it wouldn't install anything anyway.

So I purged all of my open-office from the system and reinstalled. Using my laptop which upgraded directly from v2.4 to the current 3.0 I selected all the same packages.  Everything seems to work fine except that "Formula" does not launch from it's menu entry (or by any other method). It seems it's not installed at all.

Searching through synaptic, I can't find it by it's normal name.  Does anyone know the exact package I need to add to put back "Formula" into working condition?

Phew...  That was a long story. I hope someone has the answer.

---

### Post by gettinoriginal on 2008-12-13
I am not quite understanding what you are looking for, the function wizard ??  Or are you refering to the help window when you make an incorrect "formula" ??

---

### Post by Therion on 2008-12-13
It's not called "Formula" it's called "Calc".  You can search for it in Add/Remove and it pops right up.

---

### Post by crjackson on 2008-12-13
> **Therion said:**
> It's not called "Formula" it's called "Calc".  You can search for it in Add/Remove and it pops right up.

Calc is installed and works, but Formula menu launcher does nothing..

---

### Post by Therion on 2008-12-13
Now I'm confused too.  What is this "Formula" application you are referring to?  

I've not heard of it and as far as I know there is no application in the OOO suite by that name.

---

### Post by epitaph on 2008-12-13
In the terminal try:

```
ooffice -math
```

For me, this can be added or removed using the Add/Remove Programs manager. I found it just filtering by "formula".

Err. I just realized you're using OpenOffice.org 3 while I'm still on the old 2.4, I'm assuming the process will be similar.

---

### Post by gettinoriginal on 2008-12-13
Install openoffice.org-dmaths from synaptics

---

### Post by crjackson on 2008-12-13
> **epitaph said:**
> In the terminal try:

```
ooffice -math
```

For me, this can be added or removed using the Add/Remove Programs manager. I found it just filtering by "formula".

Err. I just realized you're using OpenOffice.org 3 while I'm still on the old 2.4, I'm assuming the process will be similar.

Yeah, I have that in my menu but it won't launch.

---

### Post by crjackson on 2008-12-13
> **gettinoriginal said:**
> Install openoffice.org-dmaths from synaptics

dmaths isn't it. I already tried that, unless I did something wrong that is.

---

### Post by crjackson on 2008-12-13
Here's a screen shot from a working install. Look at the title bar, tools and math tools displayed on the page.

---

### Post by crjackson on 2008-12-13
Nevermind, I found it. It's called:

openoffice.org-math

Phew...  Thought I was going to need a re-install of the whole OS just to fix this issue... Glad that didn't happenll

---

