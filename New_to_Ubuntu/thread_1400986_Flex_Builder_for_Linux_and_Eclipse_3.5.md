---
title: "Flex Builder for Linux and Eclipse 3.5"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by AceFrehley on 2010-02-07
I installed flex builder for linux from the adobe site, and I keep getting the following error when I try to open an MXML file in eclipse 3.5. I was just wondering if anybody has run across this issue? 

As I look at the error perspective, it says "Unable to create editor ID com.adobe.flexbuilder.editors.mxml.MXMLEditor". I checked to see that the .mxml file extension is associated to the correct editor type. but it seems like that editor has not been installed by the FB plugin... I also tried including the Flex 3.5 SDK as the active Flex SDK within the IDE preferences, but didn't have any luck.

Thanks.

```


org.eclipse.jface.util.Assert$AssertionFailedException: Assertion failed: 
    at org.eclipse.jface.util.Assert.isTrue(Assert.java:179)
    at org.eclipse.jface.util.Assert.isTrue(Assert.java:164)
    at com.adobe.flexbuilder.editors.derived.editor.FlexMultiPageEditorPart.setActivePage(FlexMultiPageEditorPart.java:569)
    at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.setActivePage(CodeAndDesignEditor.java:647)
    at com.adobe.flexbuilder.editors.mxml.MXMLEditor.setActivePage(MXMLEditor.java:487)
    at com.adobe.flexbuilder.editors.derived.editor.FlexMultiPageEditorPart.createPartControl(FlexMultiPageEditorPart.java:235)
    at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.createPartControl(CodeAndDesignEditor.java:162)
    at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:662)
    at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:462)
    at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
    at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:313)
    at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:180)
    at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:270)
    at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
    at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:473)
    at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1256)
    at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1209)
    at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1608)
    at org.eclipse.ui.internal.PartStack.add(PartStack.java:499)
    at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:103)
    at org.eclipse.ui.internal.PartStack.add(PartStack.java:485)
    at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:112)
    at org.eclipse.ui.internal.EditorSashContainer.addEditor(EditorSashContainer.java:63)
    at org.eclipse.ui.internal.EditorAreaHelper.addToLayout(EditorAreaHelper.java:225)
    at org.eclipse.ui.internal.EditorAreaHelper.addEditor(EditorAreaHelper.java:213)
    at org.eclipse.ui.internal.EditorManager.createEditorTab(EditorManager.java:778)
    at org.eclipse.ui.internal.EditorManager.openEditorFromDescriptor(EditorManager.java:677)
    at org.eclipse.ui.internal.EditorManager.openEditor(EditorManager.java:638)
    at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2854)
    at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2762)
    at org.eclipse.ui.internal.WorkbenchPage.access$11(WorkbenchPage.java:2754)
    at org.eclipse.ui.internal.WorkbenchPage$10.run(WorkbenchPage.java:2705)
    at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
    at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2701)
    at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2685)
    at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2676)
    at org.eclipse.ui.ide.IDE.openEditor(IDE.java:651)
    at org.eclipse.ui.ide.IDE.openEditor(IDE.java:610)
    at org.eclipse.ui.actions.OpenFileAction.openFile(OpenFileAction.java:99)
    at org.eclipse.ui.actions.OpenSystemEditorAction.run(OpenSystemEditorAction.java:99)
    at org.eclipse.ui.views.navigator.OpenActionGroup.runDefaultAction(OpenActionGroup.java:133)
    at org.eclipse.ui.views.navigator.MainActionGroup.runDefaultAction(MainActionGroup.java:330)
    at org.eclipse.ui.views.navigator.ResourceNavigator.handleOpen(ResourceNavigator.java:787)
    at org.eclipse.ui.views.navigator.ResourceNavigator$6.open(ResourceNavigator.java:499)
    at org.eclipse.ui.OpenAndLinkWithEditorHelper$InternalListener.open(OpenAndLinkWithEditorHelper.java:48)
    at org.eclipse.jface.viewers.StructuredViewer$2.run(StructuredViewer.java:842)
    at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:42)
    at org.eclipse.core.runtime.Platform.run(Platform.java:888)
    at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:48)
    at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:175)
    at org.eclipse.jface.viewers.StructuredViewer.fireOpen(StructuredViewer.java:840)
    at org.eclipse.jface.viewers.StructuredViewer.handleOpen(StructuredViewer.java:1101)
    at org.eclipse.jface.viewers.StructuredViewer$6.handleOpen(StructuredViewer.java:1205)
    at org.eclipse.jface.util.OpenStrategy.fireOpenEvent(OpenStrategy.java:264)
    at org.eclipse.jface.util.OpenStrategy.access$2(OpenStrategy.java:258)
    at org.eclipse.jface.util.OpenStrategy$1.handleEvent(OpenStrategy.java:298)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1176)
    at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3493)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3112)
    at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2405)
    at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2369)
    at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2221)
    at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:500)
    at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:493)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1311)


```

---

### Post by Huss on 2010-02-10
I have the same issue. 

Try this thread: [http://ubuntuforums.org/showthread.php?p=8808074#post8808074](http://ubuntuforums.org/showthread.php?p=8808074#post8808074)

The AXDT plug-in hasn't work for me, but might be worth a try.

---

### Post by Huss on 2010-02-11
It's working, brilliant!

I uninstalled Flex and Ilox elixir and then re-installed. Ilog may have been the issue. 

Note: to install ilog properly I needed to temporarily rename the eclipse executable from 'eclipse' to 'Eclipse'.

---

### Post by AceFrehley on 2010-02-13
Thanks for the responses. Yes, I should probably look into the AXDT plugin. I missed this section on the flexbuilder linux site, which says that "Design View" is unsupported (guess they are intent on getting your $250.00 bucks :)

[http://labs.adobe.com/technologies/flex/flexbuilder_linux/releasenotes.html#features](http://labs.adobe.com/technologies/flex/flexbuilder_linux/releasenotes.html#features)

---

