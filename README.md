# vaadin14-lein-problem

A small project that demonstrate issue with (I guess)
[leiningen](http://leiningen.org) resolver.

## Problem description

Leiningen version: 2.9.6.

Run `lein deps` in this project. It will spin up CPU to 100%, run for
some time and exit with this error:

```edn
{:clojure.main/message
 "Execution error (OutOfMemoryError) at java.lang.reflect.Method/copy (Method.java:153).\nGC overhead limit exceeded\n",
 :clojure.main/triage
 {:clojure.error/class java.lang.OutOfMemoryError,
  :clojure.error/line 153,
  :clojure.error/cause "GC overhead limit exceeded",
  :clojure.error/symbol java.lang.reflect.Method/copy,
  :clojure.error/source "Method.java",
  :clojure.error/phase :execution},
 :clojure.main/trace
 {:via
```

Full error trace is in error-trace.edn file in this repository.

On other hand, if you generate `pom.xml` with `lein pom` and run
`mvn install`, maven will correctly download all packages.

The similar thing is done with
[tools.deps](https://github.com/clojure/tools.deps.alpha). Run
`clj -Sverbose` and will pull dependencies without problem


