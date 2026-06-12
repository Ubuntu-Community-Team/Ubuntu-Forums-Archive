---
title: "Django ModelFormset"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by navaneethan on 2011-02-01
i want to display a three same django form in a django admin page,so i came to use modelform set

but i am unable to get it what i wanted

this is my code;plz suggest it what is the issue here?

```
from django.contrib import admin
from django import forms
from tinymce import widgets
from jobs.models import Job
from jobs.models import JobTagMembership


class JobAdminForm(forms.ModelForm):
    class Meta:
        model = Job

    description = forms.CharField(widget=widgets.TinyMCE(attrs={'cols':80, 'rows':20}))

from django.forms.models import BaseModelFormSet    

class BaseJobFormSet(BaseModelFormSet):
    def __init__(self, *args, **kwargs):
        super(BaseJobFormSet, self).__init__(*args, **kwargs)
        #self.queryset = Job.objects.filter(name__startswith='O')
    #pass
from django.forms.models import modelformset_factory

#from django.forms.formsets import formset_factory
JobAdminFormSet = modelformset_factory(Job,form=JobAdminForm,formset=BaseJobFormSet,extra=2,fields=('name', 'description'))
#formset = JobAdminFormSet()
   
class JobAdmin(admin.ModelAdmin):
    formset = JobAdminFormSet()
    instances = formset.save(commit=False)
    count=0
    for instance in instances:
        count+=1
        print count
        instance.save()
    #if formset.is_valid():
    #    formset.save()
    ''' def save_formset(self, request, form, formset, change):
        instances = formset.save(commit=False)
        for instance in instances:
            instance.user = request.user
            instance.save()
        formset.save_m2m()    '''
                 
    #form = JobAdminForm
    list_display = ('name',)
   
    
class JTMAdmin(admin.ModelAdmin):
    pass



admin.site.register(Job,JobAdmin)

```

---

