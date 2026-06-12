---
title: "Only two thirds of page showing"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-01-14
Hi all,
I downloaded pouet chess which resulted in leaving me with a low resolution screen. Rebooting fixed the resolution problem but I am left with only two thirds of a normal page. F11 works O.K. for full screen and other users have a correct full page screen.
Is there a command I can use to restore full length page?

Thanks in advance!  :)

---

### Post by lionaneesh on 2011-01-14
> **aussiebean said:**
> Hi all,
I downloaded pouet chess which resulted in leaving me with a low resolution screen. Rebooting fixed the resolution problem but I am left with only two thirds of a normal page. F11 works O.K. for full screen and other users have a correct full page screen.
Is there a command I can use to restore full length page?

Thanks in advance!  :)

You can use```

xrandr -s 1024x760
```

Usage :-
```
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose



```

if facing problems with this command :-

Post the output by 'xrandr' :-
In my case its :-

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by OldBoy44 on 2011-01-14
Thanks for your reply lionaneesh but I am afraid I am a not very bright newbie and am not sure what I should do regarding entering commands.

Entering first command came up with error - Size 1024x760 not found in available modes - I'm afraid that I am not sure what to do.

I am not sure if I explained properly - It is not the screen mode that is forshortened - rather the page.

:)

---

### Post by OldBoy44 on 2011-01-14
Thanks for your reply lionaneesh but I am afraid I am a not very bright newbie and am not sure what I should do regarding entering commands.

Entering first command came up with error - Size 1024x760 not found in available modes - I'm afraid that I am not sure what to do.

I am not sure if I explained properly - It is not the screen mode that is forshortened - rather the page.

:)

---

### Post by OldBoy44 on 2011-01-14
Thanks for your reply lionaneesh but I am afraid I am a not very bright 67 year old newbie and am not sure what I should do regarding entering commands.

Entering first command came up with error - Size 1024x760 not found in available modes - I'm afraid that I am not sure what to do.

I am not sure if I explained properly - It is NOT the screen mode that is forshortened - rather the page.

Sorry for delay in replying - there was AProxy Error!

:)

---

### Post by OldBoy44 on 2011-01-14
Thanks for your reply lionaneesh but I am afraid I am a not very bright 67 year old newbie and am not sure what I should do regarding entering commands.

Entering first command came up with error - Size 1024x760 not found in available modes - I'm afraid that I am not sure what to do.

I am not sure if I explained properly - It is NOT the screen mode that is forshortened - rather the page.

Sorry for delay in replying - there was A Proxy Error!

:)

---

### Post by lionaneesh on 2011-01-14
> **aussiebean said:**
> Thanks for your reply lionaneesh but I am afraid I am a not very bright newbie and am not sure what I should do regarding entering commands.

Entering first command came up with error - Size 1024x760 not found in available modes - I'm afraid that I am not sure what to do.

I am not sure if I explained properly - It is not the screen mode that is forshortened - rather the page.

:)

Open up your terminal
and
Enter:-
xrandr

and paste your output here :-

It should be like:-

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)


```

---

### Post by OldBoy44 on 2011-01-14
Thanks for your reply lionaneesh but I am afraid I am a not very bright 67 year old newbie and am not sure what I should do regarding entering commands.

Entering first command came up with error - Size 1024x760 not found in available modes - I'm afraid that I am not sure what to do.

I am not sure if I explained properly - It is NOT the screen mode that is forshortened - rather the page.

Sorry for delay in replying - there was A Proxy Error!

:)

---

### Post by lionaneesh on 2011-01-14
> **lionaneesh said:**
> Open up your terminal
and
Enter:-
xrandr

and paste your output here :-

It should be like:-

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)


```


Hope you understand this!!!!!

---

### Post by OldBoy44 on 2011-01-14
Here it is -

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2048 x 2048
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1

  :)

---

### Post by lionaneesh on 2011-01-14
> **aussiebean said:**
> Thanks for your reply lionaneesh but I am afraid I am a not very bright 67 year old newbie and am not sure what I should do regarding entering commands.

Entering first command came up with error - Size 1024x760 not found in available modes - I'm afraid that I am not sure what to do.

I am not sure if I explained properly - It is NOT the screen mode that is forshortened - rather the page.

Sorry for delay in replying - there was A Proxy Error!

:)

Please dont repeat the same replies

---

### Post by OldBoy44 on 2011-01-14
I am very sorry, I did not realize that the posts would eventually come through following Proxy Error.


I now think the problem may be with Firefox which I am investigating.

Problem resolved - I had to reset Firefox tool bars and controls.
I will mark the thread as solved if I get the opportunity.

---

### Post by lionaneesh on 2011-01-14
> **aussiebean said:**
> Here it is -

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2048 x 2048
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1

  :)
looks normal..

---

