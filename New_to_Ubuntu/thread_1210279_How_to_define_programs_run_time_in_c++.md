---
title: "How to define programs run time in c++?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by SKYDOS on 2009-07-11
I need to test my program.
I tried this way:
begin = clock();
....my code....
end = clock();
cout<<"Time="<<(end-begin)/CLOCKS_PER_SEC<<endl;

but if my program works less then 1 sec I get "Time: 0", but I need this format [0.000] secs

how can I do such thing?

thanks.

---

### Post by Hospadar on 2009-07-11
My guess is you need to cast your values to double before doing the division, otherwise it will truncate the result.

```

begin = clock();
....my code....
end = clock();
cout<<"Time="<<**(double)**(end-begin)/**(double)**CLOCKS_PER_SEC<<endl;

```
alternatively you could declare "begin" and "end" as doubles and save CLOCKS_PER_SEC to a temporary double and you wouldn't have to cast.

Furthermore, this won't take into account any process switching time, which if you are running something multithreaded, might be important.  A wall time measure in addition might be a wise idea just to make sure you are always getting the right picture.

---

### Post by sisco311 on 2009-07-11
just use the time command:
```
time myprog
```

---

### Post by SKYDOS on 2009-07-11
> **sisco311 said:**
> just use the time command:
```
time myprog
```

cool! thanks!:guitar:

---

