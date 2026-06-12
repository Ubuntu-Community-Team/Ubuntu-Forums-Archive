---
title: "Conky : how can I configure Weather...?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by sdim on 2010-10-07
Hi, everyone.
I found a nice code for Conky, but I'm having a bit of trouble configuring the weather part. It remains empty, and so does the Music section.Any ideas as to what to do?
My location is Athens, Greece.
Here's the code included referring to the Weather.
Many thanks.
```
${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
${font}${color DimGray}

${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=GRXX0004 –datatype=GR}
${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=GRXX0004 –datatype=HT}
$font${voffset -55}${alignr}${color DimGray}Wind: ${execi 1800 conkyForecast –location=GRXX0004 –datatype=WS}
${alignr}${color DimGray}Humidity: ${execi 1800 conkyForecast –location=GRXX0004 –datatype=HM}
${alignr}${color DimGray}Precipitation: ${execi 1800 conkyForecast –location=GRXX0004 –datatype=PC}
```

---

### Post by llamabr on 2010-10-07
What have you tried to do with this code?  And, what results do you get setting your location if you just right click and set it that way?

---

### Post by Ozitraveller on 2010-10-07
[http://crunchbanglinux.org/wiki/conky](http://crunchbanglinux.org/wiki/conky)

[http://conkyhardcore.com/](http://conkyhardcore.com/)

---

### Post by sdim on 2010-10-11
The Weather part in Conky remains empty.
I took a look at an Ubuntu forum page related to that, but found no easy way to do this.Many thanks for the eagerness, guys.

---

### Post by mister_p_1998 on 2010-10-11
Dont you have to sign up to weather.com? (free)
Steve

---

