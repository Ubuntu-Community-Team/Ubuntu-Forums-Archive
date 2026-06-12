---
title: "Media problem."
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Billyh on 2009-04-27
I have just installed UBUNTU 9.04 and got no video or sound from youtube or video I reinstalled java with the plugins for firefox this gave me video from youtube but no sound although I get sound from a CD, when I load a dvd the moviplayer starts with a blank screen but then goes to a directory display of the dvd. As I don't know any thing about media playing I don't know where to start.

---

### Post by Jakey_TheSnake on 2009-04-27
Try: 

```
sudo apt-get install lame
``` 

Restart browser. 

If not, enable [[COLOR="Blue"]Third-Party sources repository[/COLOR]](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party%20Software%20Tab) and then:

```
sudo apt-get install adobe-flashplugin
```

Tell me how that goes.

---

### Post by Billyh on 2009-04-28
> **Jakey_TheSnake said:**
> Try: 

```
sudo apt-get install lame
```Restart browser. 

If not, enable [[COLOR=Blue]Third-Party sources repository[/COLOR]]("https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party%20Software%20Tab") and then:

```
sudo apt-get install adobe-flashplugin
```Tell me how that goes.

The first command worked ok.
the second said that the addobe flashplugin was already installed at the latest rev.
as for the other probs youtube still shows the video but no sound, the CD does not play any more and the DVD still goes to a directory  listing..I tried to system test which I haven't tried on 9.04 but it looked like it was loading but never did and eventualy disappeared. it did work on 8.10

I cannot get any sound from the speakers now

---

### Post by billgoldberg on 2009-04-28
Right click on the volume applet and pick "Open Volume Control".

Make sure nothing is muted:

[[img]http://xs138.xs.to/xs138/09182/screenshot222.png[/img]](http://xs.to)

Did that help?

If not, say so and we'll try something else.

---

### Post by Billyh on 2009-04-29
Yes it did but movie player still doesn't play movies

quote=billgoldberg;7167007]Right click on the volume applet and pick "Open Volume Control".

Make sure nothing is muted:

[[IMG]http://xs138.xs.to/xs138/09182/screenshot222.png[/IMG]]("http://xs.to")

Did that help?

If not, say so and we'll try something else.[/quote]
Yes it worked but the movie player still doesn't play movies thanks for putting up with a dodo.

---

### Post by Billyh on 2009-04-29
> **Billyh said:**
> This fixed the sound in youtube and CD's play again but music player doesn't play movies

quote=billgoldberg;7167007]Right click on the volume applet and pick "Open Volume Control".

Make sure nothing is muted:

[[IMG]http://xs138.xs.to/xs138/09182/screenshot222.png[/IMG]]("http://xs.to")

Did that help?

If not, say so and we'll try something else.
Unfortunately no joy:confused:[/quote]

---

