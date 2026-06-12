---
title: "Monitor Cuda and GPU on Boinc???"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by lotharjade on 2010-05-08
Is there a way to see what work your GPU is doing, and also to see if it is Boinc'in with Cuda (or GPU use by other programs)??  

Basically, I would like to see the type of info the System Monitor shows on the Resources tab (which would be a good place for it).  How much work is it doing, and possibly show on the Processes tab the percent of GPU is being used by the Boinc program.

---

### Post by Paqman on 2010-05-10
BOINC will tell you if you're using CUDA. Open the BOINC manager and look in the messages. You might need to run the benchmarks again, but if it shows that it's spotted both your CPU(s) and GPU, then you're using CUDA.

I'm not aware of any way to show GPGPU use in System Monitor. You can definitely see its effects in your BOINC stats though. If the rate you're crunching data at suddenly quadruples, that's CUDA kicking in.

---

### Post by wolfe on 2010-05-25
So is there no way to graphically view gpu utilization like in windows?

---

### Post by elgordodude on 2011-01-13
In terminal
```

nvidia-smi -a
```

---

### Post by elgordodude on 2011-01-13
In terminal
```

nvidia-smi -a
```

---

