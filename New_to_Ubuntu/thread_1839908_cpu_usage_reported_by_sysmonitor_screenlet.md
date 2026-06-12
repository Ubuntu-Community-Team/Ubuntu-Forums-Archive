---
title: "cpu usage reported by sysmonitor screenlet"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by beew on 2011-09-06
I think the sysmonitor screenlet is not working in Natty.

Here is a screenshot comparing cpu usage shown in sysmonitor screenlet and output of 'top'. I think the sysmonitor output is not even consistent as the cpu usage shown in the breakdown by process is higher than the usage reported under cpu0 and cpu1.

Is it broken or have I interpreted the numbers incorrectly?

Thanks.

---

### Post by gordintoronto on 2011-09-06
What you call sysmonitor is more likely Conky. In the .conkyrc file, it says how often to update the displayed values. Top is probably updating its display more frequently.

CPU usage changes by quite a bit from one millisecond to the next, unless you are running some heavy-duty processing. There's basically no difference between 1% and 5%.

---

### Post by beew on 2011-09-06
That is not Conkey, that is a screenlet that is "inspired by Conkey", there is no setting to adjust the rate of display.

---

