---
title: "TypeError: 'numpy.ndarray' object is not callable"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by Saad Bin Ahmed on 2011-07-13
Hey,

I am trying to execute the python program but it gives me following error

 File "./arabic_online.py", line 73, in <module>
    contain=(array(inputs)-inputMeans()/inputStds())
TypeError: 'numpy.ndarray' object is not callable

Follwing is the chunk of code where error lies.

for trace in parse(inkmlfile).getElementsByTagName('trace'):        
            for coords in trace.firstChild.nodeValue.split(','):
                pt = coords.split()
                inputs.append([float(pt[0]), float(pt[1]), 0.0])
            inputs[-1][-1] = 1
        seqLengths.append(len(inputs) - oldlen)
        seqDims.append([seqLengths[-1]])
**contain=(array(inputs)-inputMeans()/inputStds())**
inputs = contain.tolist()

Any help would be highly appreciated.

---

