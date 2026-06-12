---
title: "Problem with &quot;Reading database..&quot;"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by TuxUser0008 on 2011-08-02
When I installed GIMP it worked fine but after I tried to install desmume through terminal it just hanged after it said "Reading database.." does anyone know what this is? It seems to be affecting everything I try to install. Even when it say's "Reading database..." I can't exit terminal either when it gets to that. I try clicking on the exit button on the window but there's no response and none of my other applications seem to respond when I click on them through the unity bar? Basically it freezes my system right after I try to exit terminal. My menu bar at the top right won't pull down and unity seems to get stuck.. Is there anything I can try to somehow get things to work once again? :confused:

---

### Post by TuxUser0008 on 2011-08-02
So after letting it run for about 30-40 minutes with "Reading Database.." it finally did something though things are still very slow but I'm not sure how to speed things back up when it comes to installing software.. but anyway I'll just wait maybe see what it does. Well main problem is fixed but system is very slow.. :(

---

### Post by jtarin on 2011-08-02
If your dpkg runs seem to take a long time in the “reading database” step, try this:

Step One: Clear the available file ```
dpkg --clear-avail
```

Step Two: Forget old unavailable packages ```
dpkg --forget-old-unavail
```

---

