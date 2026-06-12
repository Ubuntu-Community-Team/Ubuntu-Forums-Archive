---
title: "Add text to image?"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by t0p on 2010-09-15
I'm not, strictly speaking, an "Absolute Beginner" (I've been a fourum member since 2007); but this is kind of a beginner-ish question.  So here goes.

I've got a nice photograph that I'd like to print and use as the front of a birthday card for someone.  Just a short text, like "HAPPY BIRTHDAY YOU OLD SO-AND-SO!!!"

I know I could use the Gimp to do this.  But that seems rather over-kill-ish to me.  I don't often pull out my bazooka to deal with flies.

So, is there a quickish, simple-ish way to add the text?

---

### Post by Jazzy_Jeff on 2010-09-15
I personally would use either Scribus or The Gimp.

---

### Post by howefield on 2010-09-15
Use the terminal command

```
convert
```

with the -draw option.

```
man convert
```

Eg, navigate to where your picture is, let's say you have one called test.jpg the command might look something like..

```
convert -pointsize 36 -fill red -draw 'text 300,300 "Happy Birthday - You old so and so" ' test.jpg test1.jpg
```

---

### Post by t0p on 2010-09-15
> **howefield said:**
> Use the terminal command

```
convert
```with the -draw option.

```
man convert
```Eg, navigate to where your picture is, let's say you have one called test.jpg the command might look something like..

```
convert -pointsize 36 -fill red -draw 'text 300,300 "Happy Birthday - You old so and so" ' test.jpg test1.jpg
```

Hi howefield.  I'm not familiar with the "convert" command; so, rather than read the manual, I did a virtual copy-n-paste of your command.  And this is the output I got:

```

t0p@deimos:~$ convert -pointsize 36 -fill red -draw 'text 300,300 "HAPPY BIRTHDAY DAMMIT!!!"test.jpg test1.jpg
> 

```

You see, it gave me a new line prefixed with a ">", like it was expecting some particular type of input.  I didn't know what to do, so I hit Ctrl-C to get out of the situation, then looked in the directory and, oops, no "test1.jpg" with my joyful greeting attached.

I don't really want to fure up an app like the Gimp to do (what I suspected of being) a simple operation.  What do other people say?

---

### Post by howefield on 2010-09-15
You might have copy/pasted the command, but you messed up the syntax after editing it.

---

### Post by kerry_s on 2010-09-15
for simple i just use mtpaint.

---

### Post by t0p on 2010-09-15
I'm so ashamed of myself.  Not long ago, I decided to see if I could live by the age-old *nix tradition of an app for a job, nice and squeezy, no cruft or mission creep allowed.  And now I've used the great big bloody Gimp to add a few words of text to a picture!!!   Shame on me!

---

### Post by jtarin on 2010-09-15
I have got to wonder at your approach to this. I wouldn't hesitate one second to fire up The Gimp to do this......that's its job doing things like this with much finer control than a command line. It would take me longer to  map out my command and execute it than to have it finished in The Gimp, but then I've been using The Gimp for years.

---

### Post by imaginashawn on 2010-09-15
Just use Gimp!

---

