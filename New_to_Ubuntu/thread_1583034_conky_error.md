---
title: "conky error"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by dzon65 on 2010-09-27
Hi.I'm getting an error for my gpu temperature.Tried two commands:nvidia temp (with the beneeth color settings) and 
${color #303030}Temp gpu: ${color #00FFFF } ${execi 60 nvidia-settings  -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'}  ${color #404040}C
Both color the temperature pink.
Edit:just found it,syntax error,closing bracket after color settings.

---

