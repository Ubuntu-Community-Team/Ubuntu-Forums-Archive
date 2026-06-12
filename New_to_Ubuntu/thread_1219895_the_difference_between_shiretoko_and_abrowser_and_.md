---
title: "the difference between shiretoko and abrowser? and which should i install?"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-22
currently im having shiretoko with ppa repos but i really dont know which is better...

---

### Post by ulidtko on 2009-07-22
Shiretoko is new, testing version of the Firefox browser. E.g. "Shiretoko" is the codename of Firefox 3.5

If you are ready to sudden surprises (as for testing, non-stable software), install Shiretoko, if not — wait until it's stable release.

---

### Post by heyyy on 2009-07-22
> **ulidtko said:**
> Shiretoko is new, testing version of the Firefox browser. E.g. "Shiretoko" is the codename of Firefox 3.5

If you are ready to sudden surprises (as for testing, non-stable software), install Shiretoko, if not &#8212; wait until it's stable release.

so you mean... that a stable release isnt out yet?

---

### Post by philinux on 2009-07-22
Someone not up to date eh. ;)

[http://www.mozilla-europe.org/en/?utm_source=google&utm_medium=ppc&utm_campaign=firefox35&gclid=CLjWurmp6ZsCFZ4A4wodlWp76A](http://www.mozilla-europe.org/en/?utm_source=google&utm_medium=ppc&utm_campaign=firefox35&gclid=CLjWurmp6ZsCFZ4A4wodlWp76A)

---

### Post by heyyy on 2009-07-22
> **philinux said:**
> Someone not up to date eh. ;)

[http://www.mozilla-europe.org/en/?utm_source=google&utm_medium=ppc&utm_campaign=firefox35&gclid=CLjWurmp6ZsCFZ4A4wodlWp76A](http://www.mozilla-europe.org/en/?utm_source=google&utm_medium=ppc&utm_campaign=firefox35&gclid=CLjWurmp6ZsCFZ4A4wodlWp76A)

ok thanks
could you give me some instructions on how to install?

---

### Post by philinux on 2009-07-22
As always the best way is from the repo.

sudo apt-get install firefox-3.5

It's called shiretoko and will appear as a menu item under app>internet.

It is 3.5.1.

It will copy your 3.0.11 profile over so both run side by side. This is because karmic in October will most likely only have 3.5 but for jaunty the devs are maintaining the two.

Good reason too as many themes and addons still have not been upgraded to work with 3.5.  Some have some haven't. I'm happy running both.

---

### Post by ulidtko on 2009-07-22
> **philinux said:**
> Someone not up to date eh. ;)

[http://www.mozilla-europe.org/en/?utm_source=google&utm_medium=ppc&utm_campaign=firefox35&gclid=CLjWurmp6ZsCFZ4A4wodlWp76A](http://www.mozilla-europe.org/en/?utm_source=google&utm_medium=ppc&utm_campaign=firefox35&gclid=CLjWurmp6ZsCFZ4A4wodlWp76A)

So i can't get in my mind, why is it still called Shiretoko rather than Firefox 3.5, even after release? It is pretty confusing to see this codename in the browser title...

---

### Post by mcduck on 2009-07-22
> **ulidtko said:**
> So i can't get in my mind, why is it still called Shiretoko rather than Firefox 3.5, even after release? It is pretty confusing to see this codename in the browser title...

Because it won't replace Firefox 3 but installs alongside it. Having different names for them should be less confusing than having two different Firefox's installed..

---

### Post by ulidtko on 2009-07-22
> **mcduck said:**
> Because it won't replace Firefox 3 but installs alongside it. Having different names for them should be less confusing than having two different Firefox's installed..

Actually, the question is not in the packaging. Firefox 3.0 is in the package firefox-3.0, Firefox 3.5 is in package firefox-3.5, so its all ok.

But why does *the window* displays in its title "%Website title% - Shiretoko"? And, btw, the window icon looks not so "firefoxish", as it should be by the first thought.

I just can't find any reasonable explanation for such things :confused:

---

### Post by heyyy on 2009-07-22
btw on the "about shiretoko" the version is 3.5.2pre is this normal?

---

### Post by ulidtko on 2009-07-22
> **heyyy said:**
> btw on the "about shiretoko" the version is 3.5.2pre is this normal?

...and i have 3.5.1 there

---

### Post by mcduck on 2009-07-22
> **ulidtko said:**
> Actually, the question is not in the packaging. Firefox 3.0 is in the package firefox-3.0, Firefox 3.5 is in package firefox-3.5, so its all ok.

But why does *the window* displays in its title "%Website title% - Shiretoko"? And, btw, the window icon looks not so "firefoxish", as it should be by the first thought.

I just can't find any reasonable explanation for such things :confused:

I wasn't talking about packaging, but the user interface. Having two versions of Firefox in your menu versus having Firefox and Shiretoko, with different icons..

Developers decided that the difference between the two should be more clear. Having two browsers with same name and almost exactly the same icon would be confusing in many situations. Thus they decided to use the development name even for the final version of FF3.5 in Jaunty's repositories. Makes sense to me, even more so when you consider that even having the FF3.5 available in Jaunty's repositories is a nice extra and not something you should expect to happen.. :)

---

### Post by ulidtko on 2009-07-22
> **mcduck said:**
> I wasn't talking about packaging, but the user interface. Having two versions of Firefox in your menu versus having Firefox and Shiretoko, with different icons..

A bit wierd as for me %) This approach makes me think that Firefox 3.5 is not a further version of The Grand Firefox Browser, but some another browser with completely different name... This brought to me a lot of confusion when i first installed and launched FF3.5

---

