---
title: "How to find the ASCII code of a character..?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-05
Can anyone say me how to find the ascii code of a character..?

---

### Post by Paresh on 2010-06-05
Use Character Map (Applications->Accessories->Character Map)

It shows the ASCII value in hex, so use the calculator if you want decimal.

---

### Post by da burger on 2010-06-05
[www.asciitable.com](www.asciitable.com)

---

### Post by karthick87 on 2010-06-05
> **Paresh said:**
> Use Character Map (Applications->Accessories->Character Map)

It shows the ASCII value in hex, so use the calculator if you want decimal.


I don get you,please explain a bit more..

---

### Post by kleskjr on 2010-06-05
if you want it automatically in many languages the command is ord('x')

---

### Post by sisco311 on 2010-06-05
bash:
```

char="A"
printf '%d\n' "'$char"
```

---

### Post by gmargo on 2010-06-05
See the **ascii(7)** man page.

---

### Post by karthick87 on 2010-06-05
> **sisco311 said:**
> bash:
```

char="A"
printf '%d\n' "'$char"
```



This helped me,thank you :)

---

