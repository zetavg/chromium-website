---
breadcrumbs:
- - /chromium-os/developer-library/reference
  - ChromiumOS > Developer Library > Reference
page_name: cpp-pref
title: C++ Prefs
---

[TOC]

Prefs is a system for storing configuration data keyed to the user session (i.e.
the sorts of data that would be stored in config files in most other software
projects). Although originally designed for storing Chrome's user preferences,
it now sees use more generally to store all sorts of feature data. It is capable
of representing any JSON data structure (strings, numbers, booleans, lists,
mappings -- see
[`base::Value`](https://source.chromium.org/chromium/chromium/src/+/main:base/values.h)).

Prefs are not meant to store large collections of data, which could result in a
large memory overhead. See more
[here](https://chromium.googlesource.com/chromium/src/+/HEAD/chrome/browser/prefs/README.md).

All prefs need to be registered by a
[PrefRegistry](https://source.chromium.org/chromium/chromium/src/+/main:components/prefs/pref_registry.h;drc=8ba1bad80dc22235693a0dd41fe55c0fd2dbdabd),
which is often triggered by
[BrowserContextKeyedServiceFactory::RegisterProfilePrefs()](https://source.chromium.org/chromium/chromium/src/+/refs/heads/main:components/keyed_service/content/browser_context_keyed_service_factory.h;l=174;drc=47042255a0d8acfbcf58cb0eea4607ec574b8419).

For prefs to be recognized in the ChromeOS UI, the pref name must be added to
`GetAllowlistedKeys()` in
[`prefs_util.cc`](https://source.chromium.org/chromium/chromium/src/+/main:chrome/browser/extensions/api/settings_private/prefs_util.cc;l=176)

To learn more about using Prefs to write code, see
go/chromium-cookbook-policy-prefs. If you'd like to understand prefs more
deeply, read ["User Sessions"](/chromium-os/developer-library/reference/user-sessions/user-sessions).
