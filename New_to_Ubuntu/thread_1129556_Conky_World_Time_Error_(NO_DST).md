---
title: "Conky World Time Error (NO DST)"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-18
I've got conky set-up and am using the following for my world time section of conky:

```

${font Arial:bold:size=12}${color Tan1}WORLD TIME ${color DarkSlateGray} ${hr 2}
$font${color Green}Boston$alignr${tztime America/Boston %T}
$font${color Green}London$alignr${tztime Europe/london %T}
$font${color Green}Kolkata$alignr${tztime Asia/Kolkata %T}
$font${color Green}Singapore$alignr${tztime Asia/Singapore %T}

```

The times show up fine, but 
London is showing up as 23:57, when it is actually 0:57
Boston is showing up as 18:57, when it is actually 19:57

Any thoughts?

---

### Post by abhiroopb on 2009-04-18
never mind, I had put in the wrong places!

---

