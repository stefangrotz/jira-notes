# Filter und Boards

## Bug management

List of filter for a Jira wall that supports a structured bug management process that works without admin rights just by the use of labels.

### All Bugs
(filter in ("All team Projects") OR assignee = "teamaccount@company.tld" OR assignee in membersOf("Auto-Domain - X")) AND type = bug

### All open Bugs
filter in ("All Bugs") AND resolution = unresolved

###  Bugs analysis in Progress
filter in ("All Bugs") AND labels in (BM_Analysis_In-Progress) AND resolution = unresolved

### Bugs analysis ready for dev

filter in ("All open Bugs") AND labels in (BM_Analysis_Ready-for-Dev) AND resolution = unresolved

### Bugs analysis to do

filter in ("All open Bugs") AND (labels is EMPTY OR labels not in (BM_Analysis_In-Progress, BM_Analysis_Waiting-for-Feedback, BM_Analysis_Ready-for-Dev)) AND resolution = unresolved

### Bugs analysis waiting for feedback

filter in ("All open Bugs"") AND labels in (BM_Analysis_Waiting-for-Feedback) AND resolution = unresolved

### Bugs - missing bug cause labels
Including a filter date to filter out previous label systems.

issueFunction in issueFieldMatch("filter in (\"All Bugs\") and resolution != unresolved and createdDate > \"2017/10/01\"", labels, "^(?!.*BC_).*$") AND resolution not in ("Cannot Reproduce", Duplicate, Incomplete, "Not An Issue", "Won't Do", "Won't Fix")

### All open bugs - No Assignee/No priority

filter in ("All Bugs") AND (assignee is EMPTY OR priority = Undefined)

### All open Bugs - no Progress
filter in ("All open Bugs) AND updated < -7d

### All resolved Bugs

filter in ("All Bugs") AND type = bug AND status = resolved

### Too old Bugs
filter in ("All open Bugs") AND created < -28d
