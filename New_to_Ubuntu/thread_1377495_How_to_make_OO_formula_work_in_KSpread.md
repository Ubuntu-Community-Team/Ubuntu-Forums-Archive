---
title: "How to make OO formula work in KSpread?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by doublewitt on 2010-01-10
Any spreadsheet enthusiastes out there...?
This formula works fine in openoffice and excel but I need to get it to work in KSpread - *it doesn't*. I thought KSpread was fully compatible. But sometimes I have to modify formulas... I'm stuck on this one:

=IF(OR(F5="",G5=""),"",H4+F5-G5)

Can anyone tell me what changes to make so I can get it to work in KSpread?

---

### Post by mechro on 2010-01-10
Just had a quick look. KSpread seems to uses semi-colons instead of commas. Try...

=IF(OR(F5="";G5="");"";H4+F5-G5)

---

### Post by doublewitt on 2010-01-10
Thank you so much - that solved it!

---

