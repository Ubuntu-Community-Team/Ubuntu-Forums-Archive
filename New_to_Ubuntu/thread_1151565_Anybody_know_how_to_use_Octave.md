---
title: "Anybody know how to use Octave?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Dapilot1 on 2009-05-07
So in MATLAB you do .^ (or .* ./ etc) so that you can multiply a some long series of with other stuff, but in QtOctave it doesn't work. Any ideas?
```

#Constants
p = .63;
r = 11;
D = 1.1;

#Variables
T = {300:.1:1000};
g = .0061 + .0047*(4/(r*D));

#Equations
t = T.^(1/2);
a = -1*(g)/(2*t)*ln(1/p);

#Graph
plot(T,a,"r");
hold on

```

P.S. I move the bad part to its own equation so I could work with it better.

---

### Post by Arndt on 2009-05-07
> **Dapilot1 said:**
> So in MATLAB you do .^ (or .* ./ etc) so that you can multiply a some long series of with other stuff, but in QtOctave it doesn't work. Any ideas?
```

#Constants
p = .63;
r = 11;
D = 1.1;

#Variables
T = {300:.1:1000};
g = .0061 + .0047*(4/(r*D));

#Equations
t = T.^(1/2);
a = -1*(g)/(2*t)*ln(1/p);

#Graph
plot(T,a,"r");
hold on

```

P.S. I move the bad part to its own equation so I could work with it better.

I don't know octave, but what happens? Is there an error message (if so, what does it say), or a wrong result?

---

### Post by jpkotta on 2009-05-14
```

#Constants
p = .63;
r = 11;
D = 1.1;

#Variables
**T = {300:.1:1000};**
g = .0061 + .0047*(4/(r*D));

#Equations
t = T.^(1/2);
[B]a = -1*(g)/(2*t)*ln(1/p);
[/B]
#Graph
plot(T,a,"r");
hold on

```

Any particular reason that T needs to be a cell?  Also, t is not a scalar, so you need dot divide (./).

---

