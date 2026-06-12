---
title: "user defined function in spreadsheet"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by sectionIV on 2010-03-18
How do I create a user defined function in a spreadsheet (openoffice.org calc, or gnumeric)? I have several groups of cells I want to average (only those that actually have values) and I'd like to specify the cells once instead of twice.

One example of the current code is

=if(iserror(average(F7:F20,J7:J20,N7:N20,R7:R20)),"",average(F7:F20,J7:J20,N7:N20,R7:R20))

I'd like to be able to specify the cells once then use the entire range multiple times in the new function

=myAvg(F7:F20,J7:J20,N7:N20,R7:R20)

Where myAvg is defined with something like

myAvg(cell_list)=if(iserror(average(cell_list),"",average(cell_list))


Any suggestions?

Thanks

---

### Post by jimv on 2010-03-25
Could you just put that value in a cell and then use that cell wherever else you need that value?

---

