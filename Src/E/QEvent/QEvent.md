# QEvent 类

QEvent 类是Qt框架中所有事件类的基类. 所有事件对象均包含若干个事件参数. [More...](https://doc.qt.io/qt-5/qevent.html#details)

| Header:       | #include <QEvent>                                            |
| ------------- | ------------------------------------------------------------ |
| qmake:        | QT += core                                                   |
| Inherited By: | [QActionEvent](https://doc.qt.io/qt-5/qactionevent.html), [QChildEvent](https://doc.qt.io/qt-5/qchildevent.html), [QCloseEvent](https://doc.qt.io/qt-5/qcloseevent.html), [QDragLeaveEvent](https://doc.qt.io/qt-5/qdragleaveevent.html), [QDropEvent](https://doc.qt.io/qt-5/qdropevent.html), [QDynamicPropertyChangeEvent](https://doc.qt.io/qt-5/qdynamicpropertychangeevent.html), [QEnterEvent](https://doc.qt.io/qt-5/qenterevent.html), [QExposeEvent](https://doc.qt.io/qt-5/qexposeevent.html), [QFileOpenEvent](https://doc.qt.io/qt-5/qfileopenevent.html), [QFocusEvent](https://doc.qt.io/qt-5/qfocusevent.html), [QGestureEvent](https://doc.qt.io/qt-5/qgestureevent.html), [QGraphicsSceneEvent](https://doc.qt.io/qt-5/qgraphicssceneevent.html), [QHelpEvent](https://doc.qt.io/qt-5/qhelpevent.html), [QHideEvent](https://doc.qt.io/qt-5/qhideevent.html), [QIconDragEvent](https://doc.qt.io/qt-5/qicondragevent.html), [QInputEvent](https://doc.qt.io/qt-5/qinputevent.html), [QInputMethodEvent](https://doc.qt.io/qt-5/qinputmethodevent.html), [QInputMethodQueryEvent](https://doc.qt.io/qt-5/qinputmethodqueryevent.html), [QMoveEvent](https://doc.qt.io/qt-5/qmoveevent.html), [QPaintEvent](https://doc.qt.io/qt-5/qpaintevent.html), [QPlatformSurfaceEvent](https://doc.qt.io/qt-5/qplatformsurfaceevent.html), [QResizeEvent](https://doc.qt.io/qt-5/qresizeevent.html), [QScrollEvent](https://doc.qt.io/qt-5/qscrollevent.html), [QScrollPrepareEvent](https://doc.qt.io/qt-5/qscrollprepareevent.html), [QShortcutEvent](https://doc.qt.io/qt-5/qshortcutevent.html), [QShowEvent](https://doc.qt.io/qt-5/qshowevent.html), [QStateMachine::SignalEvent](https://doc.qt.io/qt-5/qstatemachine-signalevent.html), [QStateMachine::WrappedEvent](https://doc.qt.io/qt-5/qstatemachine-wrappedevent.html), [QStatusTipEvent](https://doc.qt.io/qt-5/qstatustipevent.html), [QTimerEvent](https://doc.qt.io/qt-5/qtimerevent.html), [QWhatsThisClickedEvent](https://doc.qt.io/qt-5/qwhatsthisclickedevent.html), and [QWindowStateChangeEvent](https://doc.qt.io/qt-5/qwindowstatechangeevent.html) |

- [QEvent类成员，以及继承自其基类的成员列表](https://doc.qt.io/qt-5/qevent-members.html)



## 公有类型

| enum | **[类型](https://doc.qt.io/qt-5/qevent.html#Type-enum)** { None, ActionAdded, ActionChanged, ActionRemoved, ActivationChange, …, MaxUser } |
| ---- | ------------------------------------------------------------ |
|      |                                                              |



## 属性

- **[accepted](https://doc.qt.io/qt-5/qevent.html#accepted-prop)** : bool



## 公有成员函数

|              | **[QEvent](https://doc.qt.io/qt-5/qevent.html#QEvent)**(QEvent::Type *type*) |
| ------------ | ------------------------------------------------------------ |
| virtual      | **[~QEvent](https://doc.qt.io/qt-5/qevent.html#dtor.QEvent)**() |
| void         | **[accept](https://doc.qt.io/qt-5/qevent.html#accept)**()    |
| void         | **[ignore](https://doc.qt.io/qt-5/qevent.html#ignore)**()    |
| bool         | **[isAccepted](https://doc.qt.io/qt-5/qevent.html#accepted-prop)**() const |
| void         | **[setAccepted](https://doc.qt.io/qt-5/qevent.html#accepted-prop)**(bool *accepted*) |
| bool         | **[spontaneous](https://doc.qt.io/qt-5/qevent.html#spontaneous)**() const |
| QEvent::Type | **[type](https://doc.qt.io/qt-5/qevent.html#type)**() const  |



## 静态公有数据成员

| int  | **[registerEventType](https://doc.qt.io/qt-5/qevent.html#registerEventType)**(int *hint* = -1) |
| ---- | ------------------------------------------------------------ |
|      |                                                              |



## 细节描述

Qt的主事件循环 ([QCoreApplication::exec](https://doc.qt.io/qt-5/qcoreapplication.html#exec)()) 从事件队列中取出窗口系统的原生事件, 并将其转换成QEvent对象, 然后将它们传递给[QObject](https://doc.qt.io/qt-5/qobject.html)s.

通常这些事件由底层窗口系统自动传递给应用层 ([spontaneous](https://doc.qt.io/qt-5/qevent.html#spontaneous)() returns `true`), 但通过QCoreApplication::sendEvent](https://doc.qt.io/qt-5/qcoreapplication.html#sendEvent)() and [QCoreApplication::postEvent](https://doc.qt.io/qt-5/qcoreapplication.html#postEvent)() ([spontaneous](https://doc.qt.io/qt-5/qevent.html#spontaneous)() returns `false`)这两个函数也可以手动的传递事件.

[QObjects](https://doc.qt.io/qt-5/qobject.html) 通过调用它们的 [QObject::event](https://doc.qt.io/qt-5/qobject.html#event)()函数来接收事件. 此函数被声明为虚函数，它可以在QObject子类中被重新实现，从而能做到自定义事件处理过程以及增加额外的事件类型; [QWidget::event](https://doc.qt.io/qt-5/qwidget.html#event)() is a notable example. By default, events are dispatched to event handlers like [QObject::timerEvent](https://doc.qt.io/qt-5/qobject.html#timerEvent)() and [QWidget::mouseMoveEvent](https://doc.qt.io/qt-5/qwidget.html#mouseMoveEvent)(). [QObject::installEventFilter](https://doc.qt.io/qt-5/qobject.html#installEventFilter)() allows an object to intercept events destined for another object.

The basic QEvent contains only an event type parameter and an "accept" flag. The accept flag set with [accept](https://doc.qt.io/qt-5/qevent.html#accept)(), and cleared with [ignore](https://doc.qt.io/qt-5/qevent.html#ignore)(). It is set by default, but don't rely on this as subclasses may choose to clear it in their constructor.

Subclasses of QEvent contain additional parameters that describe the particular event.

**See also** [QObject::event](https://doc.qt.io/qt-5/qobject.html#event)(), [QObject::installEventFilter](https://doc.qt.io/qt-5/qobject.html#installEventFilter)(), [QCoreApplication::sendEvent](https://doc.qt.io/qt-5/qcoreapplication.html#sendEvent)(), [QCoreApplication::postEvent](https://doc.qt.io/qt-5/qcoreapplication.html#postEvent)(), and [QCoreApplication::processEvents](https://doc.qt.io/qt-5/qcoreapplication.html#processEvents)().

## Member Type Documentation

### enum QEvent::Type

This enum type defines the valid event types in Qt. The event types and the specialized classes for each type are as follows:

| Constant                                   | Value                 | Description                                                  |
| ------------------------------------------ | --------------------- | ------------------------------------------------------------ |
| `QEvent::None`                             | `0`                   | Not an event.                                                |
| `QEvent::ActionAdded`                      | `114`                 | A new action has been added ([QActionEvent](https://doc.qt.io/qt-5/qactionevent.html)). |
| `QEvent::ActionChanged`                    | `113`                 | An action has been changed ([QActionEvent](https://doc.qt.io/qt-5/qactionevent.html)). |
| `QEvent::ActionRemoved`                    | `115`                 | An action has been removed ([QActionEvent](https://doc.qt.io/qt-5/qactionevent.html)). |
| `QEvent::ActivationChange`                 | `99`                  | A widget's top-level window activation state has changed.    |
| `QEvent::ApplicationActivate`              | `121`                 | This enum has been deprecated. Use ApplicationStateChange instead. |
| `QEvent::ApplicationActivated`             | `ApplicationActivate` | This enum has been deprecated. Use ApplicationStateChange instead. |
| `QEvent::ApplicationDeactivate`            | `122`                 | This enum has been deprecated. Use ApplicationStateChange instead. |
| `QEvent::ApplicationFontChange`            | `36`                  | The default application font has changed.                    |
| `QEvent::ApplicationLayoutDirectionChange` | `37`                  | The default application layout direction has changed.        |
| `QEvent::ApplicationPaletteChange`         | `38`                  | The default application palette has changed.                 |
| `QEvent::ApplicationStateChange`           | `214`                 | The state of the application has changed.                    |
| `QEvent::ApplicationWindowIconChange`      | `35`                  | The application's icon has changed.                          |
| `QEvent::ChildAdded`                       | `68`                  | An object gets a child ([QChildEvent](https://doc.qt.io/qt-5/qchildevent.html)). |
| `QEvent::ChildPolished`                    | `69`                  | A widget child gets polished ([QChildEvent](https://doc.qt.io/qt-5/qchildevent.html)). |
| `QEvent::ChildRemoved`                     | `71`                  | An object loses a child ([QChildEvent](https://doc.qt.io/qt-5/qchildevent.html)). |
| `QEvent::Clipboard`                        | `40`                  | The clipboard contents have changed.                         |
| `QEvent::Close`                            | `19`                  | Widget was closed ([QCloseEvent](https://doc.qt.io/qt-5/qcloseevent.html)). |
| `QEvent::CloseSoftwareInputPanel`          | `200`                 | A widget wants to close the software input panel (SIP).      |
| `QEvent::ContentsRectChange`               | `178`                 | The margins of the widget's content rect changed.            |
| `QEvent::ContextMenu`                      | `82`                  | Context popup menu ([QContextMenuEvent](https://doc.qt.io/qt-5/qcontextmenuevent.html)). |
| `QEvent::CursorChange`                     | `183`                 | The widget's cursor has changed.                             |
| `QEvent::DeferredDelete`                   | `52`                  | The object will be deleted after it has cleaned up ([QDeferredDeleteEvent](https://doc.qt.io/qt-5/qdeferreddeleteevent.html)) |
| `QEvent::DragEnter`                        | `60`                  | The cursor enters a widget during a drag and drop operation ([QDragEnterEvent](https://doc.qt.io/qt-5/qdragenterevent.html)). |
| `QEvent::DragLeave`                        | `62`                  | The cursor leaves a widget during a drag and drop operation ([QDragLeaveEvent](https://doc.qt.io/qt-5/qdragleaveevent.html)). |
| `QEvent::DragMove`                         | `61`                  | A drag and drop operation is in progress ([QDragMoveEvent](https://doc.qt.io/qt-5/qdragmoveevent.html)). |
| `QEvent::Drop`                             | `63`                  | A drag and drop operation is completed ([QDropEvent](https://doc.qt.io/qt-5/qdropevent.html)). |
| `QEvent::DynamicPropertyChange`            | `170`                 | A dynamic property was added, changed, or removed from the object. |
| `QEvent::EnabledChange`                    | `98`                  | Widget's enabled state has changed.                          |
| `QEvent::Enter`                            | `10`                  | Mouse enters widget's boundaries ([QEnterEvent](https://doc.qt.io/qt-5/qenterevent.html)). |
| `QEvent::EnterEditFocus`                   | `150`                 | An editor widget gains focus for editing. `QT_KEYPAD_NAVIGATION` must be defined. |
| `QEvent::EnterWhatsThisMode`               | `124`                 | Send to toplevel widgets when the application enters "What's This?" mode. |
| `QEvent::Expose`                           | `206`                 | Sent to a window when its on-screen contents are invalidated and need to be flushed from the backing store. |
| `QEvent::FileOpen`                         | `116`                 | File open request ([QFileOpenEvent](https://doc.qt.io/qt-5/qfileopenevent.html)). |
| `QEvent::FocusIn`                          | `8`                   | Widget or Window gains keyboard focus ([QFocusEvent](https://doc.qt.io/qt-5/qfocusevent.html)). |
| `QEvent::FocusOut`                         | `9`                   | Widget or Window loses keyboard focus ([QFocusEvent](https://doc.qt.io/qt-5/qfocusevent.html)). |
| `QEvent::FocusAboutToChange`               | `23`                  | Widget or Window focus is about to change ([QFocusEvent](https://doc.qt.io/qt-5/qfocusevent.html)) |
| `QEvent::FontChange`                       | `97`                  | Widget's font has changed.                                   |
| `QEvent::Gesture`                          | `198`                 | A gesture was triggered ([QGestureEvent](https://doc.qt.io/qt-5/qgestureevent.html)). |
| `QEvent::GestureOverride`                  | `202`                 | A gesture override was triggered ([QGestureEvent](https://doc.qt.io/qt-5/qgestureevent.html)). |
| `QEvent::GrabKeyboard`                     | `188`                 | Item gains keyboard grab ([QGraphicsItem](https://doc.qt.io/qt-5/qgraphicsitem.html) only). |
| `QEvent::GrabMouse`                        | `186`                 | Item gains mouse grab ([QGraphicsItem](https://doc.qt.io/qt-5/qgraphicsitem.html) only). |
| `QEvent::GraphicsSceneContextMenu`         | `159`                 | Context popup menu over a graphics scene ([QGraphicsSceneContextMenuEvent](https://doc.qt.io/qt-5/qgraphicsscenecontextmenuevent.html)). |
| `QEvent::GraphicsSceneDragEnter`           | `164`                 | The cursor enters a graphics scene during a drag and drop operation ([QGraphicsSceneDragDropEvent](https://doc.qt.io/qt-5/qgraphicsscenedragdropevent.html)). |
| `QEvent::GraphicsSceneDragLeave`           | `166`                 | The cursor leaves a graphics scene during a drag and drop operation ([QGraphicsSceneDragDropEvent](https://doc.qt.io/qt-5/qgraphicsscenedragdropevent.html)). |
| `QEvent::GraphicsSceneDragMove`            | `165`                 | A drag and drop operation is in progress over a scene ([QGraphicsSceneDragDropEvent](https://doc.qt.io/qt-5/qgraphicsscenedragdropevent.html)). |
| `QEvent::GraphicsSceneDrop`                | `167`                 | A drag and drop operation is completed over a scene ([QGraphicsSceneDragDropEvent](https://doc.qt.io/qt-5/qgraphicsscenedragdropevent.html)). |
| `QEvent::GraphicsSceneHelp`                | `163`                 | The user requests help for a graphics scene ([QHelpEvent](https://doc.qt.io/qt-5/qhelpevent.html)). |
| `QEvent::GraphicsSceneHoverEnter`          | `160`                 | The mouse cursor enters a hover item in a graphics scene ([QGraphicsSceneHoverEvent](https://doc.qt.io/qt-5/qgraphicsscenehoverevent.html)). |
| `QEvent::GraphicsSceneHoverLeave`          | `162`                 | The mouse cursor leaves a hover item in a graphics scene ([QGraphicsSceneHoverEvent](https://doc.qt.io/qt-5/qgraphicsscenehoverevent.html)). |
| `QEvent::GraphicsSceneHoverMove`           | `161`                 | The mouse cursor moves inside a hover item in a graphics scene ([QGraphicsSceneHoverEvent](https://doc.qt.io/qt-5/qgraphicsscenehoverevent.html)). |
| `QEvent::GraphicsSceneMouseDoubleClick`    | `158`                 | Mouse press again (double click) in a graphics scene ([QGraphicsSceneMouseEvent](https://doc.qt.io/qt-5/qgraphicsscenemouseevent.html)). |
| `QEvent::GraphicsSceneMouseMove`           | `155`                 | Move mouse in a graphics scene ([QGraphicsSceneMouseEvent](https://doc.qt.io/qt-5/qgraphicsscenemouseevent.html)). |
| `QEvent::GraphicsSceneMousePress`          | `156`                 | Mouse press in a graphics scene ([QGraphicsSceneMouseEvent](https://doc.qt.io/qt-5/qgraphicsscenemouseevent.html)). |
| `QEvent::GraphicsSceneMouseRelease`        | `157`                 | Mouse release in a graphics scene ([QGraphicsSceneMouseEvent](https://doc.qt.io/qt-5/qgraphicsscenemouseevent.html)). |
| `QEvent::GraphicsSceneMove`                | `182`                 | Widget was moved ([QGraphicsSceneMoveEvent](https://doc.qt.io/qt-5/qgraphicsscenemoveevent.html)). |
| `QEvent::GraphicsSceneResize`              | `181`                 | Widget was resized ([QGraphicsSceneResizeEvent](https://doc.qt.io/qt-5/qgraphicssceneresizeevent.html)). |
| `QEvent::GraphicsSceneWheel`               | `168`                 | Mouse wheel rolled in a graphics scene ([QGraphicsSceneWheelEvent](https://doc.qt.io/qt-5/qgraphicsscenewheelevent.html)). |
| `QEvent::Hide`                             | `18`                  | Widget was hidden ([QHideEvent](https://doc.qt.io/qt-5/qhideevent.html)). |
| `QEvent::HideToParent`                     | `27`                  | A child widget has been hidden.                              |
| `QEvent::HoverEnter`                       | `127`                 | The mouse cursor enters a hover widget ([QHoverEvent](https://doc.qt.io/qt-5/qhoverevent.html)). |
| `QEvent::HoverLeave`                       | `128`                 | The mouse cursor leaves a hover widget ([QHoverEvent](https://doc.qt.io/qt-5/qhoverevent.html)). |
| `QEvent::HoverMove`                        | `129`                 | The mouse cursor moves inside a hover widget ([QHoverEvent](https://doc.qt.io/qt-5/qhoverevent.html)). |
| `QEvent::IconDrag`                         | `96`                  | The main icon of a window has been dragged away ([QIconDragEvent](https://doc.qt.io/qt-5/qicondragevent.html)). |
| `QEvent::IconTextChange`                   | `101`                 | Widget's icon text has been changed. (Deprecated)            |
| `QEvent::InputMethod`                      | `83`                  | An input method is being used ([QInputMethodEvent](https://doc.qt.io/qt-5/qinputmethodevent.html)). |
| `QEvent::InputMethodQuery`                 | `207`                 | A input method query event ([QInputMethodQueryEvent](https://doc.qt.io/qt-5/qinputmethodqueryevent.html)) |
| `QEvent::KeyboardLayoutChange`             | `169`                 | The keyboard layout has changed.                             |
| `QEvent::KeyPress`                         | `6`                   | Key press ([QKeyEvent](https://doc.qt.io/qt-5/qkeyevent.html)). |
| `QEvent::KeyRelease`                       | `7`                   | Key release ([QKeyEvent](https://doc.qt.io/qt-5/qkeyevent.html)). |
| `QEvent::LanguageChange`                   | `89`                  | The application translation changed.                         |
| `QEvent::LayoutDirectionChange`            | `90`                  | The direction of layouts changed.                            |
| `QEvent::LayoutRequest`                    | `76`                  | Widget layout needs to be redone.                            |
| `QEvent::Leave`                            | `11`                  | Mouse leaves widget's boundaries.                            |
| `QEvent::LeaveEditFocus`                   | `151`                 | An editor widget loses focus for editing. QT_KEYPAD_NAVIGATION must be defined. |
| `QEvent::LeaveWhatsThisMode`               | `125`                 | Send to toplevel widgets when the application leaves "What's This?" mode. |
| `QEvent::LocaleChange`                     | `88`                  | The system locale has changed.                               |
| `QEvent::NonClientAreaMouseButtonDblClick` | `176`                 | A mouse double click occurred outside the client area ([QMouseEvent](https://doc.qt.io/qt-5/qmouseevent.html)). |
| `QEvent::NonClientAreaMouseButtonPress`    | `174`                 | A mouse button press occurred outside the client area ([QMouseEvent](https://doc.qt.io/qt-5/qmouseevent.html)). |
| `QEvent::NonClientAreaMouseButtonRelease`  | `175`                 | A mouse button release occurred outside the client area ([QMouseEvent](https://doc.qt.io/qt-5/qmouseevent.html)). |
| `QEvent::NonClientAreaMouseMove`           | `173`                 | A mouse move occurred outside the client area ([QMouseEvent](https://doc.qt.io/qt-5/qmouseevent.html)). |
| `QEvent::MacSizeChange`                    | `177`                 | The user changed his widget sizes (macOS only).              |
| `QEvent::MetaCall`                         | `43`                  | An asynchronous method invocation via [QMetaObject::invokeMethod](https://doc.qt.io/qt-5/qmetaobject.html#invokeMethod)(). |
| `QEvent::ModifiedChange`                   | `102`                 | Widgets modification state has been changed.                 |
| `QEvent::MouseButtonDblClick`              | `4`                   | Mouse press again ([QMouseEvent](https://doc.qt.io/qt-5/qmouseevent.html)). |
| `QEvent::MouseButtonPress`                 | `2`                   | Mouse press ([QMouseEvent](https://doc.qt.io/qt-5/qmouseevent.html)). |
| `QEvent::MouseButtonRelease`               | `3`                   | Mouse release ([QMouseEvent](https://doc.qt.io/qt-5/qmouseevent.html)). |
| `QEvent::MouseMove`                        | `5`                   | Mouse move ([QMouseEvent](https://doc.qt.io/qt-5/qmouseevent.html)). |
| `QEvent::MouseTrackingChange`              | `109`                 | The mouse tracking state has changed.                        |
| `QEvent::Move`                             | `13`                  | Widget's position changed ([QMoveEvent](https://doc.qt.io/qt-5/qmoveevent.html)). |
| `QEvent::NativeGesture`                    | `197`                 | The system has detected a gesture ([QNativeGestureEvent](https://doc.qt.io/qt-5/qnativegestureevent.html)). |
| `QEvent::OrientationChange`                | `208`                 | The screens orientation has changes ([QScreenOrientationChangeEvent](https://doc.qt.io/qt-5/qscreenorientationchangeevent.html)). |
| `QEvent::Paint`                            | `12`                  | Screen update necessary ([QPaintEvent](https://doc.qt.io/qt-5/qpaintevent.html)). |
| `QEvent::PaletteChange`                    | `39`                  | Palette of the widget changed.                               |
| `QEvent::ParentAboutToChange`              | `131`                 | The widget parent is about to change.                        |
| `QEvent::ParentChange`                     | `21`                  | The widget parent has changed.                               |
| `QEvent::PlatformPanel`                    | `212`                 | A platform specific panel has been requested.                |
| `QEvent::PlatformSurface`                  | `217`                 | A native platform surface has been created or is about to be destroyed ([QPlatformSurfaceEvent](https://doc.qt.io/qt-5/qplatformsurfaceevent.html)). |
| `QEvent::Polish`                           | `75`                  | The widget is polished.                                      |
| `QEvent::PolishRequest`                    | `74`                  | The widget should be polished.                               |
| `QEvent::QueryWhatsThis`                   | `123`                 | The widget should accept the event if it has "What's This?" help ([QHelpEvent](https://doc.qt.io/qt-5/qhelpevent.html)). |
| `QEvent::ReadOnlyChange`                   | `106`                 | Widget's read-only state has changed (since Qt 5.4).         |
| `QEvent::RequestSoftwareInputPanel`        | `199`                 | A widget wants to open a software input panel (SIP).         |
| `QEvent::Resize`                           | `14`                  | Widget's size changed ([QResizeEvent](https://doc.qt.io/qt-5/qresizeevent.html)). |
| `QEvent::ScrollPrepare`                    | `204`                 | The object needs to fill in its geometry information ([QScrollPrepareEvent](https://doc.qt.io/qt-5/qscrollprepareevent.html)). |
| `QEvent::Scroll`                           | `205`                 | The object needs to scroll to the supplied position ([QScrollEvent](https://doc.qt.io/qt-5/qscrollevent.html)). |
| `QEvent::Shortcut`                         | `117`                 | Key press in child for shortcut key handling ([QShortcutEvent](https://doc.qt.io/qt-5/qshortcutevent.html)). |
| `QEvent::ShortcutOverride`                 | `51`                  | Key press in child, for overriding shortcut key handling ([QKeyEvent](https://doc.qt.io/qt-5/qkeyevent.html)). When a shortcut is about to trigger, `ShortcutOverride` is sent to the active window. This allows clients (e.g. widgets) to signal that they will handle the shortcut themselves, by accepting the event. If the shortcut override is accepted, the event is delivered as a normal key press to the focus widget. Otherwise, it triggers the shortcut action, if one exists. |
| `QEvent::Show`                             | `17`                  | Widget was shown on screen ([QShowEvent](https://doc.qt.io/qt-5/qshowevent.html)). |
| `QEvent::ShowToParent`                     | `26`                  | A child widget has been shown.                               |
| `QEvent::SockAct`                          | `50`                  | Socket activated, used to implement [QSocketNotifier](https://doc.qt.io/qt-5/qsocketnotifier.html). |
| `QEvent::StateMachineSignal`               | `192`                 | A signal delivered to a state machine ([QStateMachine::SignalEvent](https://doc.qt.io/qt-5/qstatemachine-signalevent.html)). |
| `QEvent::StateMachineWrapped`              | `193`                 | The event is a wrapper for, i.e., contains, another event ([QStateMachine::WrappedEvent](https://doc.qt.io/qt-5/qstatemachine-wrappedevent.html)). |
| `QEvent::StatusTip`                        | `112`                 | A status tip is requested ([QStatusTipEvent](https://doc.qt.io/qt-5/qstatustipevent.html)). |
| `QEvent::StyleChange`                      | `100`                 | Widget's style has been changed.                             |
| `QEvent::TabletMove`                       | `87`                  | Wacom tablet move ([QTabletEvent](https://doc.qt.io/qt-5/qtabletevent.html)). |
| `QEvent::TabletPress`                      | `92`                  | Wacom tablet press ([QTabletEvent](https://doc.qt.io/qt-5/qtabletevent.html)). |
| `QEvent::TabletRelease`                    | `93`                  | Wacom tablet release ([QTabletEvent](https://doc.qt.io/qt-5/qtabletevent.html)). |
| `QEvent::TabletEnterProximity`             | `171`                 | Wacom tablet enter proximity event ([QTabletEvent](https://doc.qt.io/qt-5/qtabletevent.html)), sent to [QApplication](https://doc.qt.io/qt-5/qapplication.html). |
| `QEvent::TabletLeaveProximity`             | `172`                 | Wacom tablet leave proximity event ([QTabletEvent](https://doc.qt.io/qt-5/qtabletevent.html)), sent to [QApplication](https://doc.qt.io/qt-5/qapplication.html). |
| `QEvent::TabletTrackingChange`             | `219`                 | The Wacom tablet tracking state has changed (since Qt 5.9).  |
| `QEvent::ThreadChange`                     | `22`                  | The object is moved to another thread. This is the last event sent to this object in the previous thread. See [QObject::moveToThread](https://doc.qt.io/qt-5/qobject.html#moveToThread)(). |
| `QEvent::Timer`                            | `1`                   | Regular timer events ([QTimerEvent](https://doc.qt.io/qt-5/qtimerevent.html)). |
| `QEvent::ToolBarChange`                    | `120`                 | The toolbar button is toggled on macOS.                      |
| `QEvent::ToolTip`                          | `110`                 | A tooltip was requested ([QHelpEvent](https://doc.qt.io/qt-5/qhelpevent.html)). |
| `QEvent::ToolTipChange`                    | `184`                 | The widget's tooltip has changed.                            |
| `QEvent::TouchBegin`                       | `194`                 | Beginning of a sequence of touch-screen or track-pad events ([QTouchEvent](https://doc.qt.io/qt-5/qtouchevent.html)). |
| `QEvent::TouchCancel`                      | `209`                 | Cancellation of touch-event sequence ([QTouchEvent](https://doc.qt.io/qt-5/qtouchevent.html)). |
| `QEvent::TouchEnd`                         | `196`                 | End of touch-event sequence ([QTouchEvent](https://doc.qt.io/qt-5/qtouchevent.html)). |
| `QEvent::TouchUpdate`                      | `195`                 | Touch-screen event ([QTouchEvent](https://doc.qt.io/qt-5/qtouchevent.html)). |
| `QEvent::UngrabKeyboard`                   | `189`                 | Item loses keyboard grab ([QGraphicsItem](https://doc.qt.io/qt-5/qgraphicsitem.html) only). |
| `QEvent::UngrabMouse`                      | `187`                 | Item loses mouse grab ([QGraphicsItem](https://doc.qt.io/qt-5/qgraphicsitem.html), [QQuickItem](https://doc.qt.io/qt-5/qquickitem.html)). |
| `QEvent::UpdateLater`                      | `78`                  | The widget should be queued to be repainted at a later time. |
| `QEvent::UpdateRequest`                    | `77`                  | The widget should be repainted.                              |
| `QEvent::WhatsThis`                        | `111`                 | The widget should reveal "What's This?" help ([QHelpEvent](https://doc.qt.io/qt-5/qhelpevent.html)). |
| `QEvent::WhatsThisClicked`                 | `118`                 | A link in a widget's "What's This?" help was clicked.        |
| `QEvent::Wheel`                            | `31`                  | Mouse wheel rolled ([QWheelEvent](https://doc.qt.io/qt-5/qwheelevent.html)). |
| `QEvent::WinEventAct`                      | `132`                 | A Windows-specific activation event has occurred.            |
| `QEvent::WindowActivate`                   | `24`                  | Window was activated.                                        |
| `QEvent::WindowBlocked`                    | `103`                 | The window is blocked by a modal dialog.                     |
| `QEvent::WindowDeactivate`                 | `25`                  | Window was deactivated.                                      |
| `QEvent::WindowIconChange`                 | `34`                  | The window's icon has changed.                               |
| `QEvent::WindowStateChange`                | `105`                 | The [window's state](https://doc.qt.io/qt-5/qwindow.html#windowState) (minimized, maximized or full-screen) has changed ([QWindowStateChangeEvent](https://doc.qt.io/qt-5/qwindowstatechangeevent.html)). |
| `QEvent::WindowTitleChange`                | `33`                  | The window title has changed.                                |
| `QEvent::WindowUnblocked`                  | `104`                 | The window is unblocked after a modal dialog exited.         |
| `QEvent::WinIdChange`                      | `203`                 | The window system identifer for this native widget has changed. |
| `QEvent::ZOrderChange`                     | `126`                 | The widget's z-order has changed. This event is never sent to top level windows. |

User events should have values between `User` and `MaxUser`:

| Constant          | Value   | Description         |
| ----------------- | ------- | ------------------- |
| `QEvent::User`    | `1000`  | User-defined event. |
| `QEvent::MaxUser` | `65535` | Last user event ID. |

For convenience, you can use the [registerEventType](https://doc.qt.io/qt-5/qevent.html#registerEventType)() function to register and reserve a custom event type for your application. Doing so will allow you to avoid accidentally re-using a custom event type already in use elsewhere in your application.

## Property Documentation

### accepted : bool

the accept flag of the event object

Setting the accept parameter indicates that the event receiver wants the event. Unwanted events might be propagated to the parent widget. By default, isAccepted() is set to true, but don't rely on this as subclasses may choose to clear it in their constructor.

For convenience, the accept flag can also be set with [accept](https://doc.qt.io/qt-5/qevent.html#accept)(), and cleared with [ignore](https://doc.qt.io/qt-5/qevent.html#ignore)().

**Access functions:**

| bool | **isAccepted**() const           |
| ---- | -------------------------------- |
| void | **setAccepted**(bool *accepted*) |

## Member Function Documentation

### QEvent::QEvent([QEvent::Type](https://doc.qt.io/qt-5/qevent.html#Type-enum) *type*)

Contructs an event object of type *type*.

### `[virtual]`QEvent::~QEvent()

Destroys the event. If it was [posted](https://doc.qt.io/qt-5/qcoreapplication.html#postEvent), it will be removed from the list of events to be posted.

### void QEvent::accept()

Sets the accept flag of the event object, the equivalent of calling [setAccepted](https://doc.qt.io/qt-5/qevent.html#accepted-prop)(true).

Setting the accept parameter indicates that the event receiver wants the event. Unwanted events might be propagated to the parent widget.

**See also** [ignore](https://doc.qt.io/qt-5/qevent.html#ignore)().

### void QEvent::ignore()

Clears the accept flag parameter of the event object, the equivalent of calling [setAccepted](https://doc.qt.io/qt-5/qevent.html#accepted-prop)(false).

Clearing the accept parameter indicates that the event receiver does not want the event. Unwanted events might be propagated to the parent widget.

**See also** [accept](https://doc.qt.io/qt-5/qevent.html#accept)().

### `[static]`int QEvent::registerEventType(int *hint* = -1)

Registers and returns a custom event type. The *hint* provided will be used if it is available, otherwise it will return a value between [QEvent::User](https://doc.qt.io/qt-5/qevent.html#Type-enum) and [QEvent::MaxUser](https://doc.qt.io/qt-5/qevent.html#Type-enum) that has not yet been registered. The *hint* is ignored if its value is not between [QEvent::User](https://doc.qt.io/qt-5/qevent.html#Type-enum) and [QEvent::MaxUser](https://doc.qt.io/qt-5/qevent.html#Type-enum).

Returns -1 if all available values are already taken or the program is shutting down.

**Note:** This function is [thread-safe](https://doc.qt.io/qt-5/threads-reentrancy.html).

This function was introduced in Qt 4.4.

### bool QEvent::spontaneous() const

Returns `true` if the event originated outside the application (a system event); otherwise returns `false`.

The return value of this function is not defined for paint events.

### [QEvent::Type](https://doc.qt.io/qt-5/qevent.html#Type-enum) QEvent::type() const

Returns the event type.