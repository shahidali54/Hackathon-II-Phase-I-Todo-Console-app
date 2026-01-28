<!-- SYNC IMPACT REPORT:
Version change: N/A (initial version) → 1.0.0
Added sections: All sections (initial constitution creation)
Removed sections: None
Templates requiring updates: N/A
Follow-up TODOs: None
-->
# Todo Full-Stack Web Application Constitution

## Core Principles

### Correctness
All features must match the defined requirements exactly. Implementation must fulfill specifications without deviation or assumption. Ensures reliable, predictable behavior that meets user expectations.

### Security-first
Authentication, authorization, and data isolation are mandatory. Every access point must enforce proper security controls. Protects user data and system integrity from unauthorized access.

### Spec-driven
All development must follow Spec-Kit Plus and Claude Code workflows. Every feature begins with a specification before implementation. Ensures consistent, well-planned development that aligns with project goals.

### Simplicity
Prefer clear, maintainable solutions over clever but complex ones. Code should be readable and understandable by team members. Reduces maintenance burden and improves long-term sustainability.

### Reliability
System must behave consistently across frontend and backend. All components should work together seamlessly without unexpected failures. Provides stable user experience and reduces operational issues.

### API Design Standard
Fully RESTful, predictable endpoints, proper HTTP status codes. All API endpoints must follow REST conventions and return appropriate status codes. Enables predictable client-server interactions and standard error handling.

### Data Integrity
All task operations must enforce user ownership. Every task operation must verify the user has rights to perform the action. Prevents unauthorized data manipulation and maintains data consistency.

## Key Standards

### Auth Standard
JWT-based authentication using Better Auth + FastAPI. Authentication tokens must be validated using shared secrets. Ensures secure, stateless authentication across the application stack.

### Code Quality
Lint-free, type-safe where applicable, readable structure. All code must pass linting checks and use appropriate typing. Maintains high code quality and reduces runtime errors.

### Error Handling
Meaningful errors, no silent failures. All errors must be properly logged and communicated to clients. Ensures proper debugging capability and user feedback.

## Constraints

### Technology Stack
- Frontend: Next.js 16+ (App Router)
- Backend: Python FastAPI
- ORM: SQLModel
- Database: Neon Serverless PostgreSQL
- Authentication: Better Auth with JWT
All implementations must use these specified technologies. Ensures consistent tech stack and interoperability.

### Authentication Requirement
All endpoints require valid JWT token after auth integration. Any request without a valid token must be rejected. Maintains security posture across the entire API surface.

## Security Rules

### JWT Token Requirement
No request without JWT token is allowed (401 Unauthorized). Every API request must include a valid JWT token in the Authorization header. Prevents unauthorized access to protected resources.

### JWT Verification
JWT must be verified using shared secret (BETTER_AUTH_SECRET). Tokens must be cryptographically validated before processing requests. Ensures token authenticity and prevents tampering.

### User Identification
Backend must extract user from token, never trust client user_id. User identity must come from verified JWT claims, not client-provided data. Prevents privilege escalation and identity spoofing.

### Query Filtering
Every DB query must be filtered by authenticated user. All database operations must include user-specific filters. Maintains data isolation between users.

### Token Expiration
Tokens must support expiration and proper refresh mechanisms. JWTs must include expiration times and be validated accordingly. Prevents long-lived access tokens from becoming security risks.

## Constraints on Behavior

### User Task Access
Users can only see their own tasks. Task retrieval queries must be filtered by the authenticated user. Maintains privacy and data separation between users.

### User Task Modification
Users can only modify/delete their own tasks. Any modification request must verify user ownership of the target task. Prevents unauthorized data manipulation.

### Access Control
Invalid access attempts must return 403 Forbidden. Requests for resources the user doesn't own must return appropriate error codes. Provides clear feedback for unauthorized access attempts.

### Token Validation
Missing/invalid tokens must return 401 Unauthorized. Requests without valid tokens must be rejected with appropriate status codes. Ensures proper authentication enforcement.

## Success Criteria

### End-to-End Functionality
All basic-level task features work end-to-end. All required functionality must be implemented and tested across the full stack. Validates that the system meets functional requirements.

### Multi-User Isolation
Multi-user isolation is enforced everywhere. Each user can only access their own data regardless of request method. Ensures proper security and privacy implementation.

### JWT Authentication
JWT auth works between Next.js and FastAPI. Authentication tokens must be properly issued, transmitted, and validated across the frontend-backend boundary. Enables secure communication between application layers.

### Data Protection
No user can access another user's data. Comprehensive checks prevent cross-user data access through any endpoint. Validates security implementation effectiveness.

### Database Integration
System runs using Neon DB with persistent storage. All data operations must work reliably with the Neon PostgreSQL database. Ensures proper data persistence and retrieval.

### Security Testing
Passes manual security testing for auth and ownership checks. System must withstand testing for authentication bypasses and data access violations. Validates security implementation completeness.

## Governance

All development must comply with these constitutional principles. Any deviation requires explicit amendment to this document with justification. All pull requests and code reviews must verify adherence to these principles. The constitution supersedes all other practices and guidelines in case of conflict.

**Version**: 1.0.0 | **Ratified**: 2026-01-19 | **Last Amended**: 2026-01-19