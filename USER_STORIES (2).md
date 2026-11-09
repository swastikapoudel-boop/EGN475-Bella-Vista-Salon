# Bella Vista Salon: User Stories and Acceptance Criteria

**Project:** EGN 475 -- Bella Vista Salon, Coral Gables\
**Backlog:** Week 2 -- Assignment 2.1

## Project Context

This prioritized backlog describes client and receptionist needs for the
Bella Vista Salon Flask prototype. Each story has a user role, goal, and
benefit, with observable Given/When/Then acceptance criteria. Edge cases
are included to make expected behavior testable.

## Prioritized User Story Backlog

### US-01 --- MUST: View Active Salon Services

As a salon client, I want to view the salon's active services,
descriptions, and estimated durations, so that I can choose a service
that meets my needs.

-   **Acceptance criterion 1:** Given the salon has services marked
    active and available for booking, When I open the services page,
    Then each active service displays its name, description, and
    estimated duration.
-   **Acceptance criterion 2 (edge case):** Given the salon has no
    services marked active, When I open the services page, Then a clear
    no-services message appears and inactive services are not displayed.

### US-02 --- MUST: View Available Appointment Time Slots

As a salon client, I want to view appointment time slots available on a
selected date for a selected service, so that I can choose a time that
can accommodate that service.

-   **Acceptance criterion 1:** Given I select an active service and a
    future date, When I view availability, Then the system displays only
    unbooked slots with enough time to complete the selected service
    during salon business hours.
-   **Acceptance criterion 2 (edge case):** Given no unbooked slot can
    accommodate the selected service on that date, When I view
    availability, Then the system displays a no-availability message and
    does not offer an unsuitable or booked slot.

### US-03 --- MUST: Submit an Appointment Request

As a salon client, I want to submit an appointment request for a
selected active service and available future time, so that I can request
a salon visit that fits my schedule.

-   **Acceptance criterion 1:** Given I have selected an active service
    and an available future slot and completed all required appointment
    fields (client name and contact information), When I submit the
    form, Then the system saves exactly one appointment request with
    pending status.
-   **Acceptance criterion 2 (edge case):** Given the client name or
    contact information is blank, the selected date/time is not in the
    future, or the slot has become unavailable, When I submit the form,
    Then the system does not save the request and displays a message
    identifying the specific validation error or scheduling conflict.

### US-04 --- MUST: Review My Appointments

As a salon client, I want to review the appointment requests associated
with my client account and their statuses, so that I can check whether
the salon has confirmed my visit.

-   **Acceptance criterion 1:** Given I am signed in to a client account
    associated with appointment requests, When I open My Appointments,
    Then I see the date, time, service, and status for each appointment
    associated with that account.
-   **Acceptance criterion 2 (edge case):** Given I am signed in and my
    account has no appointments, When I open My Appointments, Then a
    no-appointments message appears and no other client's records are
    shown.

### US-05 --- MUST: View the Staff Schedule

As a salon receptionist, I want to view appointments for a selected
calendar date in time order, so that I can organize the salon's workday.

-   **Acceptance criterion 1:** Given appointments exist for the
    selected calendar date, When I open the staff schedule for that
    date, Then the schedule lists each appointment's time, client,
    service, and status in chronological order.
-   **Acceptance criterion 2 (edge case):** Given no appointments exist
    for the selected calendar date, When I open the staff schedule, Then
    a clear empty-state message appears without an error.

### US-06 --- MUST: Confirm a Pending Appointment

As a salon receptionist, I want to confirm a pending appointment, so
that the client knows the salon has accepted the request.

-   **Acceptance criterion 1:** Given an appointment has pending status,
    When I select Confirm for that appointment, Then its status changes
    to confirmed and the updated status is displayed.
-   **Acceptance criterion 2 (edge case):** Given an appointment is
    cancelled or completed, When I attempt to confirm it, Then the
    system rejects the change and preserves the existing status. Given
    it is already confirmed, When I select Confirm again, Then the
    system leaves it confirmed and displays that no status change was
    needed.

### US-07 --- MUST: Cancel an Appointment

As a salon receptionist, I want to cancel a pending or confirmed
appointment, so that the schedule reflects appointments that will no
longer take place.

-   **Acceptance criterion 1:** Given an appointment has pending or
    confirmed status, When I select Cancel and confirm the action, Then
    its status changes to cancelled and its time is released for
    availability, provided it is still in the future.
-   **Acceptance criterion 2 (edge case):** Given an appointment is
    already completed or cancelled, When I attempt to cancel it again,
    Then the system prevents the invalid action and preserves the
    existing status.

### US-08 --- SHOULD: Mark an Appointment as Completed

As a salon receptionist, I want to mark a confirmed appointment as
completed after its scheduled service has taken place, so that the salon
keeps an accurate record of finished visits.

-   **Acceptance criterion 1:** Given an appointment is confirmed and
    its scheduled end time has passed, When I select Mark Completed,
    Then its status changes to completed.
-   **Acceptance criterion 2 (edge case):** Given an appointment is
    pending, cancelled, or already completed, or its scheduled end time
    has not passed, When I attempt to mark it completed, Then the system
    rejects the change and preserves the existing status.

### US-09 --- SHOULD: Add a Salon Service

As a salon receptionist, I want to add a new salon service with its
details, so that clients can see the new service before booking.

-   **Acceptance criterion 1:** Given I enter a nonblank service name
    that is not already in use (ignoring capitalization and
    leading/trailing spaces), a description, and a positive whole-number
    duration in minutes, When I save the new service, Then it is added
    to the active services list with the entered details.
-   **Acceptance criterion 2 (edge case):** Given the service name is
    blank or duplicated, or the duration is not a positive whole number,
    When I save the new service, Then the system rejects the entry,
    identifies the invalid field, and does not create a duplicate
    service.

### US-10 --- SHOULD: Update an Existing Salon Service

As a salon receptionist, I want to update an existing salon service's
name, description, or duration, so that clients see accurate and current
service information.

-   **Acceptance criterion 1:** Given I select an existing service and
    enter a nonblank name that is unique among other services (ignoring
    capitalization and leading/trailing spaces), a description, and a
    positive whole-number duration in minutes, When I save the changes,
    Then the selected service displays the updated details.
-   **Acceptance criterion 2 (edge case):** Given the service no longer
    exists, the revised name is blank or duplicates another service, or
    the duration is not a positive whole number, When I save the
    changes, Then the system rejects the update, identifies the invalid
    field or missing service, and preserves the existing details.

### US-11 --- COULD: Display an Appointment Receipt Message

As a salon client, I want to see a receipt message after submitting an
appointment request, so that I know whether the request was received.

-   **Acceptance criterion 1:** Given a valid appointment request has
    been saved successfully, When submission finishes, Then I see a
    receipt message confirming that the request was received and is
    pending.
-   **Acceptance criterion 2 (edge case):** Given the request is
    rejected by validation or a scheduling conflict, or the system
    cannot save it because of a server or database error, When
    submission finishes unsuccessfully, Then I see an error message and
    no success receipt.

## Priority Summary

-   **MUST:** US-01 through US-07 (7 stories).
-   **SHOULD:** US-08 through US-10 (3 stories).
-   **COULD:** US-11 (1 story).

**Total:** 11 stories, including six receptionist/staff stories (US-05
through US-10). The MUST stories cover the essential client booking
journey and core receptionist scheduling actions. Appointment completion
and service maintenance are SHOULD priorities. A separate receipt
message is COULD because it improves feedback but is secondary to saving
and managing a valid appointment.

## INVEST Review and Refinement

The backlog was reviewed against Independent, Negotiable, Valuable,
Estimable, Small, and Testable. The actual Copilot review found the
stories generally focused and suitable in structure, but identified
undefined terms, validation details, status-transition edge cases, and
an authentication dependency.

-   **US-01:** Defined active services as services marked active and
    available for booking.
-   **US-02:** Clarified that availability is calculated for a selected
    service and must accommodate its duration within business hours.
-   **US-03:** Specified required client name and contact information,
    future date/time validation, and rejection of a slot that becomes
    unavailable before submission.
-   **US-04:** Kept the authenticated-account requirement explicit and
    identified authentication/account association as a dependency not
    otherwise specified in this backlog. No authentication story was
    invented.
-   **US-05:** Clarified that the selected date is a calendar date.
-   **US-06:** Added behavior for confirming an appointment that is
    already confirmed.
-   **US-07:** Clarified that cancelling a future appointment releases
    its time for availability.
-   **US-08:** Defined completion eligibility using the scheduled end
    time and addressed already-completed and not-yet-finished
    appointments.
-   **US-09 and US-10:** Defined service-name uniqueness as
    case-insensitive after trimming spaces and duration as a positive
    whole number of minutes. Duplicate names and invalid updates are
    rejected.
-   **US-11:** Specified validation, scheduling-conflict, and
    server/database save failures as unsuccessful submissions that must
    not show a success receipt.

These clarifications define observable prototype behavior. If
implementation uses different business rules, those rules should be
agreed with the instructor/stakeholder and reflected consistently in the
stories and tests.

## Actual GitHub Copilot Review

**Prompt used:**

> I am working on my EGN 475 Week 2 Assignment 2.1 for a Flask prototype
> called Bella Vista Salon, located in Coral Gables. Please review the
> user stories in my USER_STORIES.md file against the INVEST criteria.
> Identify stories that are too large, vague, or not testable; missing
> edge cases; and numbering or priority inconsistencies. Do not rewrite
> or modify the file. List problems only, using the story IDs, and state
> whether the backlog is suitable for the assignment.

**Copilot review summary:** Copilot reported that the stories
consistently use a user role, goal, and benefit and that each has two
Given/When/Then criteria. It found the backlog generally focused and
suitable in structure, with improvement areas involving undefined terms,
validation details, status-transition edge cases, and the authentication
dependency in US-04. It found no numbering or priority-count
inconsistency: 11 consecutive stories, seven MUST, three SHOULD, one
COULD, and six receptionist stories.

**Decisions and changes made:** The findings were accepted where they
improved clarity and testability. The stories and acceptance criteria
above were refined to define active services, availability, required
fields, account association, appointment status transitions, service
validation, and submission failures. No new authentication feature was
invented; the dependency is explicitly disclosed. Copilot did not edit
the file; the student applied the refinements.

## Questions and Answers

### 1. Which story did you split into smaller stories, and why?

I divided the broad appointment-booking journey into separate stories:
US-01 covers viewing services, US-02 covers checking availability, US-03
covers submitting an appointment request, and US-04 covers reviewing
appointments. This makes each outcome easier to estimate, prioritize,
implement, and test. I also separated confirming from cancelling
appointments (US-06 and US-07), and adding from updating services (US-09
and US-10), because each action has a distinct outcome and validation
rules.

### 2. Which story was hardest to write acceptance criteria for? What made it hard?

US-03, submitting an appointment request, was the hardest because a time
slot can be taken by another client while the first client is completing
the form. The criteria therefore cover missing required information, a
date/time that is not in the future, and a last-second scheduling
conflict. The system must reject the conflict rather than create a
double booking.

## Repository Submission

**Repository:**
https://github.com/swastikapoudel-boop/EGN475-Bella-Vista-Salon

Save this file as `USER_STORIES.md` in the repository root, then commit
and push it to the `main` branch.

**Suggested commit message:**
`Refine user stories using Copilot INVEST review`
