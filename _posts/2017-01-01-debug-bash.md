---
title: 'Debug bash'
---

# Debug bash

When bash exit abnormally, it does not prints the line where errors occur.The code snippet below solves this problem:

```bash
set -eEo pipefail
errtrap () {
    es=${PIPE_STATUS[@]}
    echo "Error in $1 line $2, status code $es"
}
trap 'errtrap ${BASH_SOURCE[0]} $LINENO' ERR
```
